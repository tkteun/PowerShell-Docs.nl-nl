---
external help file: PSModule-help.xml
keywords: powershell,cmdlet
Locale: en-US
Module Name: PowerShellGet
ms.date: 02/27/2020
online version: https://docs.microsoft.com/powershell/module/powershellget/get-installedmodule?view=powershell-7.1&WT.mc_id=ps-gethelp
schema: 2.0.0
title: Get-InstalledModule
ms.openlocfilehash: 9d4ec71a5f754b1fba090129d026d38bd32a8bc1
ms.sourcegitcommit: 9b28fb9a3d72655bb63f62af18b3a5af6a05cd3f
ms.translationtype: MT
ms.contentlocale: nl-NL
ms.lasthandoff: 07/07/2020
ms.locfileid: "93250867"
---
# <span data-ttu-id="a97ba-103">Get-InstalledModule</span><span class="sxs-lookup"><span data-stu-id="a97ba-103">Get-InstalledModule</span></span>

## <span data-ttu-id="a97ba-104">SAMENVATTING</span><span class="sxs-lookup"><span data-stu-id="a97ba-104">SYNOPSIS</span></span>
<span data-ttu-id="a97ba-105">Hiermee wordt een lijst met modules opgehaald op de computer die is geïnstalleerd door PowerShellGet.</span><span class="sxs-lookup"><span data-stu-id="a97ba-105">Gets a list of modules on the computer that were installed by PowerShellGet.</span></span>

## <span data-ttu-id="a97ba-106">SYNTAXIS</span><span class="sxs-lookup"><span data-stu-id="a97ba-106">SYNTAX</span></span>

```
Get-InstalledModule [[-Name] <String[]>] [-MinimumVersion <String>] [-RequiredVersion <String>]
 [-MaximumVersion <String>] [-AllVersions] [-AllowPrerelease] [<CommonParameters>]
```

## <span data-ttu-id="a97ba-107">BESCHRIJVING</span><span class="sxs-lookup"><span data-stu-id="a97ba-107">DESCRIPTION</span></span>

<span data-ttu-id="a97ba-108">De `Get-InstalledModule` cmdlet haalt Power shell-modules op die zijn geïnstalleerd op een computer met behulp van PowerShellGet.</span><span class="sxs-lookup"><span data-stu-id="a97ba-108">The `Get-InstalledModule` cmdlet gets PowerShell modules that are installed on a computer using PowerShellGet.</span></span> <span data-ttu-id="a97ba-109">Als u alle modules die op het systeem zijn geïnstalleerd wilt weer geven, gebruikt u de `Get-Module -ListAvailable` opdracht.</span><span class="sxs-lookup"><span data-stu-id="a97ba-109">To see all modules installed on the system, use the `Get-Module -ListAvailable` command.</span></span>

## <span data-ttu-id="a97ba-110">VOORBEELDEN</span><span class="sxs-lookup"><span data-stu-id="a97ba-110">EXAMPLES</span></span>

### <span data-ttu-id="a97ba-111">Voor beeld 1: alle geïnstalleerde modules ophalen</span><span class="sxs-lookup"><span data-stu-id="a97ba-111">Example 1: Get all installed modules</span></span>

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

<span data-ttu-id="a97ba-112">Met deze opdracht worden alle geïnstalleerde modules opgehaald.</span><span class="sxs-lookup"><span data-stu-id="a97ba-112">This command gets all installed modules.</span></span>

### <span data-ttu-id="a97ba-113">Voor beeld 2: specifieke versies van een module ophalen</span><span class="sxs-lookup"><span data-stu-id="a97ba-113">Example 2: Get specific versions of a module</span></span>

```powershell
Get-InstalledModule -Name "AzureRM.Automation" -MinimumVersion 1.0 -MaximumVersion 2.0
```

```Output
Version    Name                                Type       Repository     Description
-------    ----                                ----       ----------     -----------
1.0.1      AzureRM.Automation                  Module     PSGallery      Microsoft Azure PowerShell - Automation service cmdlets for Azure Resource Manager
```

<span data-ttu-id="a97ba-114">Met deze opdracht worden versies van de module AzureRM. Automation van versie 1,0 tot versie 2,0.</span><span class="sxs-lookup"><span data-stu-id="a97ba-114">This command gets versions of the AzureRM.Automation module from version 1.0 through version 2.0.</span></span>

## <span data-ttu-id="a97ba-115">PARAMETERS</span><span class="sxs-lookup"><span data-stu-id="a97ba-115">PARAMETERS</span></span>

### <span data-ttu-id="a97ba-116">-AllowPrerelease</span><span class="sxs-lookup"><span data-stu-id="a97ba-116">-AllowPrerelease</span></span>

<span data-ttu-id="a97ba-117">Bevat de resultaten modules die als een voorlopige versie zijn gemarkeerd.</span><span class="sxs-lookup"><span data-stu-id="a97ba-117">Includes in the results modules marked as a prerelease.</span></span>

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

### <span data-ttu-id="a97ba-118">-AllVersions</span><span class="sxs-lookup"><span data-stu-id="a97ba-118">-AllVersions</span></span>

<span data-ttu-id="a97ba-119">Hiermee wordt aangegeven dat u alle beschik bare versies van een module wilt ophalen.</span><span class="sxs-lookup"><span data-stu-id="a97ba-119">Indicates that you want to get all available versions of a module.</span></span>
<span data-ttu-id="a97ba-120">U kunt de para meter **AllVersions** niet gebruiken met de para meters **MinimumVersion** , **MaximumVersion** of **RequiredVersion** .</span><span class="sxs-lookup"><span data-stu-id="a97ba-120">You cannot use the **AllVersions** parameter with the **MinimumVersion** , **MaximumVersion** , or **RequiredVersion** parameters.</span></span>

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

### <span data-ttu-id="a97ba-121">-MaximumVersion</span><span class="sxs-lookup"><span data-stu-id="a97ba-121">-MaximumVersion</span></span>

<span data-ttu-id="a97ba-122">Hiermee geeft u de maximale of nieuwste versie van een module op die u wilt ophalen.</span><span class="sxs-lookup"><span data-stu-id="a97ba-122">Specifies the maximum, or newest, version of a module to get.</span></span> <span data-ttu-id="a97ba-123">De para meters **MaximumVersion** en **RequiredVersion** sluiten elkaar wederzijds uit. u kunt niet beide para meters in dezelfde opdracht gebruiken.</span><span class="sxs-lookup"><span data-stu-id="a97ba-123">The **MaximumVersion** and **RequiredVersion** parameters are mutually exclusive; you cannot use both parameters in the same command.</span></span>

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

### <span data-ttu-id="a97ba-124">-MinimumVersion</span><span class="sxs-lookup"><span data-stu-id="a97ba-124">-MinimumVersion</span></span>

<span data-ttu-id="a97ba-125">Hiermee geeft u de minimum versie op van één module die moet worden opgehaald.</span><span class="sxs-lookup"><span data-stu-id="a97ba-125">Specifies the minimum version of a single module to get.</span></span> <span data-ttu-id="a97ba-126">De para meters **MinimumVersion** en **RequiredVersion** sluiten elkaar wederzijds uit. u kunt niet beide para meters in dezelfde opdracht gebruiken.</span><span class="sxs-lookup"><span data-stu-id="a97ba-126">The **MinimumVersion** and **RequiredVersion** parameters are mutually exclusive; you cannot use both parameters in the same command.</span></span>

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

### <span data-ttu-id="a97ba-127">-Name</span><span class="sxs-lookup"><span data-stu-id="a97ba-127">-Name</span></span>

<span data-ttu-id="a97ba-128">Hiermee geeft u een matrix met namen van modules op die moet worden opgehaald.</span><span class="sxs-lookup"><span data-stu-id="a97ba-128">Specifies an array of names of modules to get.</span></span>

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

### <span data-ttu-id="a97ba-129">-RequiredVersion</span><span class="sxs-lookup"><span data-stu-id="a97ba-129">-RequiredVersion</span></span>

<span data-ttu-id="a97ba-130">Hiermee geeft u de exacte versie op van een module die u wilt ophalen.</span><span class="sxs-lookup"><span data-stu-id="a97ba-130">Specifies the exact version of a module to get.</span></span>

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

### <span data-ttu-id="a97ba-131">CommonParameters</span><span class="sxs-lookup"><span data-stu-id="a97ba-131">CommonParameters</span></span>

<span data-ttu-id="a97ba-132">Deze cmdlet biedt ondersteuning voor de meest gebruikte parameters: -Debug, - ErrorAction, - ErrorVariable, - InformationAction, -InformationVariable, - OutVariable,-OutBuffer, - PipelineVariable - Verbose, - WarningAction en -WarningVariable.</span><span class="sxs-lookup"><span data-stu-id="a97ba-132">This cmdlet supports the common parameters: -Debug, -ErrorAction, -ErrorVariable, -InformationAction, -InformationVariable, -OutVariable, -OutBuffer, -PipelineVariable, -Verbose, -WarningAction, and -WarningVariable.</span></span> <span data-ttu-id="a97ba-133">Zie [about_CommonParameters](../Microsoft.PowerShell.Core/About/about_CommonParameters.md)voor meer informatie.</span><span class="sxs-lookup"><span data-stu-id="a97ba-133">For more information, see [about_CommonParameters](../Microsoft.PowerShell.Core/About/about_CommonParameters.md).</span></span>

## <span data-ttu-id="a97ba-134">INVOER</span><span class="sxs-lookup"><span data-stu-id="a97ba-134">INPUTS</span></span>

### <span data-ttu-id="a97ba-135">System.String[]</span><span class="sxs-lookup"><span data-stu-id="a97ba-135">System.String[]</span></span>

### <span data-ttu-id="a97ba-136">System. String</span><span class="sxs-lookup"><span data-stu-id="a97ba-136">System.String</span></span>

## <span data-ttu-id="a97ba-137">UITVOER</span><span class="sxs-lookup"><span data-stu-id="a97ba-137">OUTPUTS</span></span>

### <span data-ttu-id="a97ba-138">System. Management. Automation. PSCustomObject</span><span class="sxs-lookup"><span data-stu-id="a97ba-138">System.Management.Automation.PSCustomObject</span></span>

## <span data-ttu-id="a97ba-139">OPMERKINGEN</span><span class="sxs-lookup"><span data-stu-id="a97ba-139">NOTES</span></span>

## <span data-ttu-id="a97ba-140">GERELATEERDE KOPPELINGEN</span><span class="sxs-lookup"><span data-stu-id="a97ba-140">RELATED LINKS</span></span>
