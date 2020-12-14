---
external help file: PSModule-help.xml
Locale: en-US
Module Name: PowerShellGet
ms.date: 02/27/2020
online version: https://docs.microsoft.com/powershell/module/powershellget/get-installedmodule?view=powershell-7.2&WT.mc_id=ps-gethelp
schema: 2.0.0
title: Get-InstalledModule
ms.openlocfilehash: 33621a89f846ca277c21aaf0ad8cd788b428da33
ms.sourcegitcommit: 95d41698c7a2450eeb70ef2fb6507fe7e6eff3b6
ms.translationtype: MT
ms.contentlocale: nl-NL
ms.lasthandoff: 11/17/2020
ms.locfileid: "94705991"
---
# <span data-ttu-id="d8537-102">Get-InstalledModule</span><span class="sxs-lookup"><span data-stu-id="d8537-102">Get-InstalledModule</span></span>

## <span data-ttu-id="d8537-103">SAMENVATTING</span><span class="sxs-lookup"><span data-stu-id="d8537-103">SYNOPSIS</span></span>
<span data-ttu-id="d8537-104">Hiermee wordt een lijst met modules opgehaald op de computer die is geïnstalleerd door PowerShellGet.</span><span class="sxs-lookup"><span data-stu-id="d8537-104">Gets a list of modules on the computer that were installed by PowerShellGet.</span></span>

## <span data-ttu-id="d8537-105">SYNTAXIS</span><span class="sxs-lookup"><span data-stu-id="d8537-105">SYNTAX</span></span>

```
Get-InstalledModule [[-Name] <String[]>] [-MinimumVersion <String>] [-RequiredVersion <String>]
 [-MaximumVersion <String>] [-AllVersions] [-AllowPrerelease] [<CommonParameters>]
```

## <span data-ttu-id="d8537-106">BESCHRIJVING</span><span class="sxs-lookup"><span data-stu-id="d8537-106">DESCRIPTION</span></span>

<span data-ttu-id="d8537-107">De `Get-InstalledModule` cmdlet haalt Power shell-modules op die zijn geïnstalleerd op een computer met behulp van PowerShellGet.</span><span class="sxs-lookup"><span data-stu-id="d8537-107">The `Get-InstalledModule` cmdlet gets PowerShell modules that are installed on a computer using PowerShellGet.</span></span> <span data-ttu-id="d8537-108">Als u alle modules die op het systeem zijn geïnstalleerd wilt weer geven, gebruikt u de `Get-Module -ListAvailable` opdracht.</span><span class="sxs-lookup"><span data-stu-id="d8537-108">To see all modules installed on the system, use the `Get-Module -ListAvailable` command.</span></span>

## <span data-ttu-id="d8537-109">VOORBEELDEN</span><span class="sxs-lookup"><span data-stu-id="d8537-109">EXAMPLES</span></span>

### <span data-ttu-id="d8537-110">Voor beeld 1: alle geïnstalleerde modules ophalen</span><span class="sxs-lookup"><span data-stu-id="d8537-110">Example 1: Get all installed modules</span></span>

```powershell
Get-InstalledModule
```

```Output
Version    Name                                Type       Repository     Description
-------    ----                                ----       ----------     -----------
2.0.0      PSGTEST-UploadMultipleVersionOfP... Module     GalleryINT     Module for DAC functionality
1.3.5      AzureAutomationDebug                Module     PSGallery      Module for debugging Azure Automation runbooks, emulating AA native cmdlets
1.0.1      AzureRM.Automation                  Module     PSGallery      Microsoft Azure PowerShell - Automation service cmdlets for Azure Resource Manager
```

<span data-ttu-id="d8537-111">Met deze opdracht worden alle geïnstalleerde modules opgehaald.</span><span class="sxs-lookup"><span data-stu-id="d8537-111">This command gets all installed modules.</span></span>

### <span data-ttu-id="d8537-112">Voor beeld 2: specifieke versies van een module ophalen</span><span class="sxs-lookup"><span data-stu-id="d8537-112">Example 2: Get specific versions of a module</span></span>

```powershell
Get-InstalledModule -Name "AzureRM.Automation" -MinimumVersion 1.0 -MaximumVersion 2.0
```

```Output
Version    Name                                Type       Repository     Description
-------    ----                                ----       ----------     -----------
1.0.1      AzureRM.Automation                  Module     PSGallery      Microsoft Azure PowerShell - Automation service cmdlets for Azure Resource Manager
```

<span data-ttu-id="d8537-113">Met deze opdracht worden versies van de module AzureRM. Automation van versie 1,0 tot versie 2,0.</span><span class="sxs-lookup"><span data-stu-id="d8537-113">This command gets versions of the AzureRM.Automation module from version 1.0 through version 2.0.</span></span>

## <span data-ttu-id="d8537-114">PARAMETERS</span><span class="sxs-lookup"><span data-stu-id="d8537-114">PARAMETERS</span></span>

### <span data-ttu-id="d8537-115">-AllowPrerelease</span><span class="sxs-lookup"><span data-stu-id="d8537-115">-AllowPrerelease</span></span>

<span data-ttu-id="d8537-116">Bevat de resultaten modules die als een voorlopige versie zijn gemarkeerd.</span><span class="sxs-lookup"><span data-stu-id="d8537-116">Includes in the results modules marked as a prerelease.</span></span>

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

### <span data-ttu-id="d8537-117">-AllVersions</span><span class="sxs-lookup"><span data-stu-id="d8537-117">-AllVersions</span></span>

<span data-ttu-id="d8537-118">Hiermee wordt aangegeven dat u alle beschik bare versies van een module wilt ophalen.</span><span class="sxs-lookup"><span data-stu-id="d8537-118">Indicates that you want to get all available versions of a module.</span></span>
<span data-ttu-id="d8537-119">U kunt de para meter **AllVersions** niet gebruiken met de para meters **MinimumVersion**, **MaximumVersion** of **RequiredVersion** .</span><span class="sxs-lookup"><span data-stu-id="d8537-119">You cannot use the **AllVersions** parameter with the **MinimumVersion**, **MaximumVersion**, or **RequiredVersion** parameters.</span></span>

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

### <span data-ttu-id="d8537-120">-MaximumVersion</span><span class="sxs-lookup"><span data-stu-id="d8537-120">-MaximumVersion</span></span>

<span data-ttu-id="d8537-121">Hiermee geeft u de maximale of nieuwste versie van een module op die u wilt ophalen.</span><span class="sxs-lookup"><span data-stu-id="d8537-121">Specifies the maximum, or newest, version of a module to get.</span></span> <span data-ttu-id="d8537-122">De para meters **MaximumVersion** en **RequiredVersion** sluiten elkaar wederzijds uit. u kunt niet beide para meters in dezelfde opdracht gebruiken.</span><span class="sxs-lookup"><span data-stu-id="d8537-122">The **MaximumVersion** and **RequiredVersion** parameters are mutually exclusive; you cannot use both parameters in the same command.</span></span>

```yaml
Type: System.String
Parameter Sets: (All)
Aliases:

Required: False
Position: Named
Default value: None
Accept pipeline input: True (ByPropertyName)
Accept wildcard characters: False
```

### <span data-ttu-id="d8537-123">-MinimumVersion</span><span class="sxs-lookup"><span data-stu-id="d8537-123">-MinimumVersion</span></span>

<span data-ttu-id="d8537-124">Hiermee geeft u de minimum versie op van één module die moet worden opgehaald.</span><span class="sxs-lookup"><span data-stu-id="d8537-124">Specifies the minimum version of a single module to get.</span></span> <span data-ttu-id="d8537-125">De para meters **MinimumVersion** en **RequiredVersion** sluiten elkaar wederzijds uit. u kunt niet beide para meters in dezelfde opdracht gebruiken.</span><span class="sxs-lookup"><span data-stu-id="d8537-125">The **MinimumVersion** and **RequiredVersion** parameters are mutually exclusive; you cannot use both parameters in the same command.</span></span>

```yaml
Type: System.String
Parameter Sets: (All)
Aliases:

Required: False
Position: Named
Default value: None
Accept pipeline input: True (ByPropertyName)
Accept wildcard characters: False
```

### <span data-ttu-id="d8537-126">-Name</span><span class="sxs-lookup"><span data-stu-id="d8537-126">-Name</span></span>

<span data-ttu-id="d8537-127">Hiermee geeft u een matrix met namen van modules op die moet worden opgehaald.</span><span class="sxs-lookup"><span data-stu-id="d8537-127">Specifies an array of names of modules to get.</span></span>

```yaml
Type: System.String[]
Parameter Sets: (All)
Aliases:

Required: False
Position: 0
Default value: None
Accept pipeline input: True (ByPropertyName)
Accept wildcard characters: False
```

### <span data-ttu-id="d8537-128">-RequiredVersion</span><span class="sxs-lookup"><span data-stu-id="d8537-128">-RequiredVersion</span></span>

<span data-ttu-id="d8537-129">Hiermee geeft u de exacte versie op van een module die u wilt ophalen.</span><span class="sxs-lookup"><span data-stu-id="d8537-129">Specifies the exact version of a module to get.</span></span>

```yaml
Type: System.String
Parameter Sets: (All)
Aliases:

Required: False
Position: Named
Default value: None
Accept pipeline input: True (ByPropertyName)
Accept wildcard characters: False
```

### <span data-ttu-id="d8537-130">CommonParameters</span><span class="sxs-lookup"><span data-stu-id="d8537-130">CommonParameters</span></span>

<span data-ttu-id="d8537-131">Deze cmdlet biedt ondersteuning voor de meest gebruikte parameters: -Debug, - ErrorAction, - ErrorVariable, - InformationAction, -InformationVariable, - OutVariable,-OutBuffer, - PipelineVariable - Verbose, - WarningAction en -WarningVariable.</span><span class="sxs-lookup"><span data-stu-id="d8537-131">This cmdlet supports the common parameters: -Debug, -ErrorAction, -ErrorVariable, -InformationAction, -InformationVariable, -OutVariable, -OutBuffer, -PipelineVariable, -Verbose, -WarningAction, and -WarningVariable.</span></span> <span data-ttu-id="d8537-132">Zie [about_CommonParameters](../Microsoft.PowerShell.Core/About/about_CommonParameters.md)voor meer informatie.</span><span class="sxs-lookup"><span data-stu-id="d8537-132">For more information, see [about_CommonParameters](../Microsoft.PowerShell.Core/About/about_CommonParameters.md).</span></span>

## <span data-ttu-id="d8537-133">INVOER</span><span class="sxs-lookup"><span data-stu-id="d8537-133">INPUTS</span></span>

### <span data-ttu-id="d8537-134">System.String[]</span><span class="sxs-lookup"><span data-stu-id="d8537-134">System.String[]</span></span>

### <span data-ttu-id="d8537-135">System. String</span><span class="sxs-lookup"><span data-stu-id="d8537-135">System.String</span></span>

## <span data-ttu-id="d8537-136">UITVOER</span><span class="sxs-lookup"><span data-stu-id="d8537-136">OUTPUTS</span></span>

### <span data-ttu-id="d8537-137">System. Management. Automation. PSCustomObject</span><span class="sxs-lookup"><span data-stu-id="d8537-137">System.Management.Automation.PSCustomObject</span></span>

## <span data-ttu-id="d8537-138">OPMERKINGEN</span><span class="sxs-lookup"><span data-stu-id="d8537-138">NOTES</span></span>

## <span data-ttu-id="d8537-139">GERELATEERDE KOPPELINGEN</span><span class="sxs-lookup"><span data-stu-id="d8537-139">RELATED LINKS</span></span>

