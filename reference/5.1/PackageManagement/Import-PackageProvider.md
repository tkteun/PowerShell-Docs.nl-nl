---
external help file: Microsoft.PowerShell.PackageManagement.dll-Help.xml
keywords: powershell,cmdlet
Locale: en-US
Module Name: PackageManagement
ms.date: 06/09/2017
online version: https://docs.microsoft.com/powershell/module/packagemanagement/import-packageprovider?view=powershell-5.1&WT.mc_id=ps-gethelp
schema: 2.0.0
title: Import-PackageProvider
ms.openlocfilehash: 1ff00ea134c442e2bdb926d12ebbfa02098d6104
ms.sourcegitcommit: 9b28fb9a3d72655bb63f62af18b3a5af6a05cd3f
ms.translationtype: MT
ms.contentlocale: nl-NL
ms.lasthandoff: 07/07/2020
ms.locfileid: "93250268"
---
# <span data-ttu-id="f8024-103">Import-PackageProvider</span><span class="sxs-lookup"><span data-stu-id="f8024-103">Import-PackageProvider</span></span>

## <span data-ttu-id="f8024-104">SAMENVATTING</span><span class="sxs-lookup"><span data-stu-id="f8024-104">SYNOPSIS</span></span>
<span data-ttu-id="f8024-105">Voegt pakket beheer pakket providers toe aan de huidige sessie.</span><span class="sxs-lookup"><span data-stu-id="f8024-105">Adds Package Management package providers to the current session.</span></span>

## <span data-ttu-id="f8024-106">SYNTAXIS</span><span class="sxs-lookup"><span data-stu-id="f8024-106">SYNTAX</span></span>

```
Import-PackageProvider [-Name] <String[]> [-RequiredVersion <String>] [-MinimumVersion <String>]
 [-MaximumVersion <String>] [-Force] [-ForceBootstrap] [<CommonParameters>]
```

## <span data-ttu-id="f8024-107">BESCHRIJVING</span><span class="sxs-lookup"><span data-stu-id="f8024-107">DESCRIPTION</span></span>

<span data-ttu-id="f8024-108">De `Import-PackageProvider` cmdlet voegt een of meer pakket providers toe aan de huidige sessie.</span><span class="sxs-lookup"><span data-stu-id="f8024-108">The `Import-PackageProvider` cmdlet adds one or more package providers to the current session.</span></span>
<span data-ttu-id="f8024-109">De provider die u importeert, moet op de lokale computer zijn geïnstalleerd.</span><span class="sxs-lookup"><span data-stu-id="f8024-109">The provider that you import must be installed on the local computer.</span></span>

<span data-ttu-id="f8024-110">Voer uit om een lijst met beschik bare providers te verkrijgen `Get-PackageProvider -ListAvailable` .</span><span class="sxs-lookup"><span data-stu-id="f8024-110">To get a list of available providers, run `Get-PackageProvider -ListAvailable`.</span></span>
<span data-ttu-id="f8024-111">Houd er rekening mee dat de naam van een pakket provider kan afwijken van de module naam.</span><span class="sxs-lookup"><span data-stu-id="f8024-111">Note that a package provider name can be different from its module name.</span></span>

<span data-ttu-id="f8024-112">Om veiligheids redenen vereist **Package Management** dat C#-providers een bevatten `provider.manifest` .</span><span class="sxs-lookup"><span data-stu-id="f8024-112">Due to security reasons, **PackageManagement** requires C#-based providers to contain a `provider.manifest`.</span></span> <span data-ttu-id="f8024-113">`provider.manifest`Zie de `.csproj` Project bestanden op voor meer informatie over het bouwen van een provider met injected [https://github.com/oneget/oneget](https://github.com/oneget/oneget) .</span><span class="sxs-lookup"><span data-stu-id="f8024-113">For more information on how to build a provider with `provider.manifest` injected, see the `.csproj` project files on [https://github.com/oneget/oneget](https://github.com/oneget/oneget).</span></span>

## <span data-ttu-id="f8024-114">VOORBEELDEN</span><span class="sxs-lookup"><span data-stu-id="f8024-114">EXAMPLES</span></span>

### <span data-ttu-id="f8024-115">Voor beeld 1: een pakket provider importeren van de lokale computer</span><span class="sxs-lookup"><span data-stu-id="f8024-115">Example 1: Import a package provider from the local computer</span></span>

```powershell
PS C:\> Import-PackageProvider -Name "Nuget"
```

<span data-ttu-id="f8024-116">Met deze opdracht wordt de Nuget-provider geïmporteerd nadat deze is geïnstalleerd op de lokale computer.</span><span class="sxs-lookup"><span data-stu-id="f8024-116">This command imports the Nuget provider after it has been installed on the local computer.</span></span>

### <span data-ttu-id="f8024-117">Voor beeld 2: een specifieke versie van een pakket provider importeren</span><span class="sxs-lookup"><span data-stu-id="f8024-117">Example 2: Import a specific version of a package provider</span></span>

```powershell
PS C:\> Find-PackageProvider -Name "Nuget" -AllVersions
Install-PackageProvider -Name "Nuget" -RequiredVersion "2.8.5.201" -Force
Get-PackageProvider -ListAvailable
Import-PackageProvider -Name "Nuget" -RequiredVersion "2.8.5.201" -Verbose
```

<span data-ttu-id="f8024-118">Met deze opdracht wordt een specifieke versie van de Nuget-pakket provider gevonden, geïnstalleerd en geïmporteerd.</span><span class="sxs-lookup"><span data-stu-id="f8024-118">This command finds, installs, and imports a specific version of the Nuget package provider.</span></span>

## <span data-ttu-id="f8024-119">PARAMETERS</span><span class="sxs-lookup"><span data-stu-id="f8024-119">PARAMETERS</span></span>

### <span data-ttu-id="f8024-120">-Force</span><span class="sxs-lookup"><span data-stu-id="f8024-120">-Force</span></span>

<span data-ttu-id="f8024-121">Hiermee wordt de opdracht uitgevoerd zonder dat de gebruiker om bevestiging wordt gevraagd.</span><span class="sxs-lookup"><span data-stu-id="f8024-121">Forces the command to run without asking for user confirmation.</span></span>
<span data-ttu-id="f8024-122">Hiermee wordt een pakket provider opnieuw geïmporteerd.</span><span class="sxs-lookup"><span data-stu-id="f8024-122">Re-imports a package provider.</span></span>

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

### <span data-ttu-id="f8024-123">-ForceBootstrap</span><span class="sxs-lookup"><span data-stu-id="f8024-123">-ForceBootstrap</span></span>

<span data-ttu-id="f8024-124">Geeft aan dat deze cmdlet pakket beheer afdwingt om de pakket provider automatisch te installeren.</span><span class="sxs-lookup"><span data-stu-id="f8024-124">Indicates that this cmdlet forces Package Management to automatically install the package provider.</span></span>

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

### <span data-ttu-id="f8024-125">-MaximumVersion</span><span class="sxs-lookup"><span data-stu-id="f8024-125">-MaximumVersion</span></span>

<span data-ttu-id="f8024-126">Hiermee geeft u de Maxi maal toegestane versie van de pakket provider die u wilt importeren.</span><span class="sxs-lookup"><span data-stu-id="f8024-126">Specifies the maximum allowed version of the package provider that you want to import.</span></span> <span data-ttu-id="f8024-127">Als u deze para meter niet toevoegt, wordt `Import-PackageProvider` de hoogste beschik bare versie van de provider geïmporteerd.</span><span class="sxs-lookup"><span data-stu-id="f8024-127">If you do not add this parameter, `Import-PackageProvider` imports the highest available version of the provider.</span></span>

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

### <span data-ttu-id="f8024-128">-MinimumVersion</span><span class="sxs-lookup"><span data-stu-id="f8024-128">-MinimumVersion</span></span>

<span data-ttu-id="f8024-129">Hiermee geeft u de mini maal toegestane versie van de pakket provider die u wilt importeren.</span><span class="sxs-lookup"><span data-stu-id="f8024-129">Specifies the minimum allowed version of the package provider that you want to import.</span></span> <span data-ttu-id="f8024-130">Als u deze para meter niet toevoegt, wordt `Import-PackageProvider` de hoogste beschik bare versie van het pakket geïmporteerd die ook voldoet aan de maximum versie die is opgegeven met behulp van de para meter *MaximumVersion* .</span><span class="sxs-lookup"><span data-stu-id="f8024-130">If you do not add this parameter, `Import-PackageProvider` imports the highest available version of the package that also satisfies any maximum version that is specified using the *MaximumVersion* parameter.</span></span>

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

### <span data-ttu-id="f8024-131">-Name</span><span class="sxs-lookup"><span data-stu-id="f8024-131">-Name</span></span>

<span data-ttu-id="f8024-132">Hiermee geeft u een of meer pakket provider namen op.</span><span class="sxs-lookup"><span data-stu-id="f8024-132">Specifies one or more package provider names.</span></span> <span data-ttu-id="f8024-133">Joker tekens zijn niet toegestaan.</span><span class="sxs-lookup"><span data-stu-id="f8024-133">Wildcards are not permitted.</span></span>

```yaml
Type: System.String[]
Parameter Sets: (All)
Aliases:

Required: True
Position: 0
Default value: None
Accept pipeline input: True (ByPropertyName)
Accept wildcard characters: False
```

### <span data-ttu-id="f8024-134">-RequiredVersion</span><span class="sxs-lookup"><span data-stu-id="f8024-134">-RequiredVersion</span></span>

<span data-ttu-id="f8024-135">Hiermee geeft u de exacte versie van de pakket provider die u wilt importeren.</span><span class="sxs-lookup"><span data-stu-id="f8024-135">Specifies the exact version of the package provider that you want to import.</span></span> <span data-ttu-id="f8024-136">Als u deze para meter niet toevoegt, wordt `Import-PackageProvider` de hoogste beschik bare versie van de provider geïmporteerd die ook voldoet aan de maximum versie die is opgegeven met behulp van de para meter **MaximumVersion** .</span><span class="sxs-lookup"><span data-stu-id="f8024-136">If you do not add this parameter, `Import-PackageProvider` imports the highest available version of the provider that also satisfies any maximum version specified using the **MaximumVersion** parameter.</span></span>

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

### <span data-ttu-id="f8024-137">CommonParameters</span><span class="sxs-lookup"><span data-stu-id="f8024-137">CommonParameters</span></span>

<span data-ttu-id="f8024-138">Deze cmdlet biedt ondersteuning voor de meest gebruikte parameters: -Debug, - ErrorAction, - ErrorVariable, - InformationAction, -InformationVariable, - OutVariable,-OutBuffer, - PipelineVariable - Verbose, - WarningAction en -WarningVariable.</span><span class="sxs-lookup"><span data-stu-id="f8024-138">This cmdlet supports the common parameters: -Debug, -ErrorAction, -ErrorVariable, -InformationAction, -InformationVariable, -OutVariable, -OutBuffer, -PipelineVariable, -Verbose, -WarningAction, and -WarningVariable.</span></span> <span data-ttu-id="f8024-139">Zie [about_CommonParameters](https://go.microsoft.com/fwlink/?LinkID=113216)voor meer informatie.</span><span class="sxs-lookup"><span data-stu-id="f8024-139">For more information, see [about_CommonParameters](https://go.microsoft.com/fwlink/?LinkID=113216).</span></span>

## <span data-ttu-id="f8024-140">INVOER</span><span class="sxs-lookup"><span data-stu-id="f8024-140">INPUTS</span></span>

### <span data-ttu-id="f8024-141">Micro soft. package management. Implementation. package provider</span><span class="sxs-lookup"><span data-stu-id="f8024-141">Microsoft.PackageManagement.Implementation.PackageProvider</span></span>

<span data-ttu-id="f8024-142">U kunt een **package provider** -object dat wordt geretourneerd door `Get-PackageProvider` in `Import-PackageProvider` .</span><span class="sxs-lookup"><span data-stu-id="f8024-142">You can pipe a **PackageProvider** object returned by `Get-PackageProvider` into `Import-PackageProvider`.</span></span>

## <span data-ttu-id="f8024-143">UITVOER</span><span class="sxs-lookup"><span data-stu-id="f8024-143">OUTPUTS</span></span>

## <span data-ttu-id="f8024-144">OPMERKINGEN</span><span class="sxs-lookup"><span data-stu-id="f8024-144">NOTES</span></span>

## <span data-ttu-id="f8024-145">GERELATEERDE KOPPELINGEN</span><span class="sxs-lookup"><span data-stu-id="f8024-145">RELATED LINKS</span></span>

[<span data-ttu-id="f8024-146">about_PackageManagement</span><span class="sxs-lookup"><span data-stu-id="f8024-146">about_PackageManagement</span></span>](../Microsoft.PowerShell.Core/About/about_PackageManagement.md)

[<span data-ttu-id="f8024-147">Registratie ongedaan maken-PackageSource</span><span class="sxs-lookup"><span data-stu-id="f8024-147">Unregister-PackageSource</span></span>](Unregister-PackageSource.md)

[<span data-ttu-id="f8024-148">Get-PackageSource</span><span class="sxs-lookup"><span data-stu-id="f8024-148">Get-PackageSource</span></span>](Get-PackageSource.md)

[<span data-ttu-id="f8024-149">REGI ster-PackageSource</span><span class="sxs-lookup"><span data-stu-id="f8024-149">Register-PackageSource</span></span>](Register-PackageSource.md)

[<span data-ttu-id="f8024-150">Get-PackageProvider</span><span class="sxs-lookup"><span data-stu-id="f8024-150">Get-PackageProvider</span></span>](Get-PackageProvider.md)
