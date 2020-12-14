---
external help file: Microsoft.PowerShell.PackageManagement.dll-Help.xml
Locale: en-US
Module Name: PackageManagement
ms.date: 06/09/2017
online version: https://docs.microsoft.com/powershell/module/packagemanagement/get-packageprovider?view=powershell-7.2&WT.mc_id=ps-gethelp
schema: 2.0.0
title: Get-PackageProvider
ms.openlocfilehash: fd8325f1a68755ee1b5c05719a04e71b22a7e9fd
ms.sourcegitcommit: 22c93550c87af30c4895fcb9e9dd65e30d60ada0
ms.translationtype: MT
ms.contentlocale: nl-NL
ms.lasthandoff: 11/19/2020
ms.locfileid: "94889487"
---
# <span data-ttu-id="656aa-102">Get-PackageProvider</span><span class="sxs-lookup"><span data-stu-id="656aa-102">Get-PackageProvider</span></span>

## <span data-ttu-id="656aa-103">SAMENVATTING</span><span class="sxs-lookup"><span data-stu-id="656aa-103">SYNOPSIS</span></span>
<span data-ttu-id="656aa-104">Retourneert een lijst met pakket providers die zijn verbonden met pakket beheer.</span><span class="sxs-lookup"><span data-stu-id="656aa-104">Returns a list of package providers that are connected to Package Management.</span></span>

## <span data-ttu-id="656aa-105">SYNTAXIS</span><span class="sxs-lookup"><span data-stu-id="656aa-105">SYNTAX</span></span>

```
Get-PackageProvider [[-Name] <String[]>] [-ListAvailable] [-Force] [-ForceBootstrap] [<CommonParameters>]
```

## <span data-ttu-id="656aa-106">BESCHRIJVING</span><span class="sxs-lookup"><span data-stu-id="656aa-106">DESCRIPTION</span></span>

<span data-ttu-id="656aa-107">De cmdlet **Get-package provider** retourneert een lijst met pakket providers die zijn verbonden met pakket beheer.</span><span class="sxs-lookup"><span data-stu-id="656aa-107">The **Get-PackageProvider** cmdlet returns a list of package providers that are connected to Package Management.</span></span>
<span data-ttu-id="656aa-108">Voor beelden van deze providers zijn PSModule, NuGet en Choco lade.</span><span class="sxs-lookup"><span data-stu-id="656aa-108">Examples of these providers include PSModule, NuGet, and Chocolatey.</span></span>
<span data-ttu-id="656aa-109">U kunt de resultaten filteren op basis van alle of een deel van een of meer provider namen.</span><span class="sxs-lookup"><span data-stu-id="656aa-109">You can filter the results based on all or part of one or more provider names.</span></span>

## <span data-ttu-id="656aa-110">VOORBEELDEN</span><span class="sxs-lookup"><span data-stu-id="656aa-110">EXAMPLES</span></span>

### <span data-ttu-id="656aa-111">Voor beeld 1: alle momenteel geladen pakket providers ophalen</span><span class="sxs-lookup"><span data-stu-id="656aa-111">Example 1: Get all currently loaded package providers</span></span>

```
PS C:\> Get-PackageProvider
```

<span data-ttu-id="656aa-112">Met deze opdracht wordt een lijst opgehaald van alle pakket providers die momenteel zijn geladen op de lokale computer.</span><span class="sxs-lookup"><span data-stu-id="656aa-112">This command gets a list of all the package providers that are currently loaded on the local computer.</span></span>

### <span data-ttu-id="656aa-113">Voor beeld 2: alle beschik bare pakket providers ophalen</span><span class="sxs-lookup"><span data-stu-id="656aa-113">Example 2: Get all available package providers</span></span>

```
PS C:\> Get-PackageProvider -ListAvailable
```

<span data-ttu-id="656aa-114">Met deze opdracht wordt een lijst opgehaald van alle pakket providers die beschikbaar zijn op de lokale computer.</span><span class="sxs-lookup"><span data-stu-id="656aa-114">This command gets a list of all package providers that are available on the local computer.</span></span>

### <span data-ttu-id="656aa-115">Voor beeld 3: dynamisch een pakket provider ophalen</span><span class="sxs-lookup"><span data-stu-id="656aa-115">Example 3: Dynamically get a package provider</span></span>

```
PS C:\> Get-PackageProvider -Name "Chocolatey" -ForceBootstrap
```

<span data-ttu-id="656aa-116">Met deze opdracht wordt de chocolade-provider automatisch geïnstalleerd als de chocolade-provider niet is geïnstalleerd op de computer.</span><span class="sxs-lookup"><span data-stu-id="656aa-116">This command automatically installs the Chocolatey provider if your computer does not have the Chocolatey provider installed.</span></span>

## <span data-ttu-id="656aa-117">PARAMETERS</span><span class="sxs-lookup"><span data-stu-id="656aa-117">PARAMETERS</span></span>

### <span data-ttu-id="656aa-118">-Force</span><span class="sxs-lookup"><span data-stu-id="656aa-118">-Force</span></span>

<span data-ttu-id="656aa-119">Geeft aan dat deze cmdlet alle andere acties met deze cmdlet afdwingt die kunnen worden geforceerd.</span><span class="sxs-lookup"><span data-stu-id="656aa-119">Indicates that this cmdlet forces all other actions with this cmdlet that can be forced.</span></span>
<span data-ttu-id="656aa-120">In **Get-package provider** betekent dit dat de para meter *Forces* hetzelfde is als de para meter *ForceBootstrap* .</span><span class="sxs-lookup"><span data-stu-id="656aa-120">In **Get-PackageProvider**, this means the *Force* parameter acts the same as the *ForceBootstrap* parameter.</span></span>

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

### <span data-ttu-id="656aa-121">-ForceBootstrap</span><span class="sxs-lookup"><span data-stu-id="656aa-121">-ForceBootstrap</span></span>

<span data-ttu-id="656aa-122">Geeft aan dat deze cmdlet pakket beheer afdwingt om de pakket provider automatisch te installeren.</span><span class="sxs-lookup"><span data-stu-id="656aa-122">Indicates that this cmdlet forces Package Management to automatically install the package provider.</span></span>

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

### <span data-ttu-id="656aa-123">-ListAvailable</span><span class="sxs-lookup"><span data-stu-id="656aa-123">-ListAvailable</span></span>

<span data-ttu-id="656aa-124">Hiermee worden alle geïnstalleerde providers opgehaald.</span><span class="sxs-lookup"><span data-stu-id="656aa-124">Gets all installed providers.</span></span>
<span data-ttu-id="656aa-125">**Get-package provider** haalt de provider op in paden die worden vermeld in de omgevings variabele **PSModulePath** en de assembly mappen van de pakket provider:</span><span class="sxs-lookup"><span data-stu-id="656aa-125">**Get-PackageProvider** gets provider in paths listed in the **PSModulePath** environment variable as well as the package provider assembly folders:</span></span>

<span data-ttu-id="656aa-126">**$env:P rogramFiles\PackageManagement\ProviderAssemblies \* \* \* \* $env: LOCALAPPDATA\PackageManagement\ProviderAssemblies**</span><span class="sxs-lookup"><span data-stu-id="656aa-126">**$env:ProgramFiles\PackageManagement\ProviderAssemblies\*\*\*\*$env:LOCALAPPDATA\PackageManagement\ProviderAssemblies**</span></span>

<span data-ttu-id="656aa-127">Zonder deze para meter worden met **Get-package provider** alleen de providers opgehaald die in de huidige sessie zijn geladen.</span><span class="sxs-lookup"><span data-stu-id="656aa-127">Without this parameter, **Get-PackageProvider** gets only the providers loaded in the current session.</span></span>

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

### <span data-ttu-id="656aa-128">-Name</span><span class="sxs-lookup"><span data-stu-id="656aa-128">-Name</span></span>

<span data-ttu-id="656aa-129">Hiermee geeft u een of meer provider namen of gedeeltelijke provider namen op.</span><span class="sxs-lookup"><span data-stu-id="656aa-129">Specifies one or more provider names, or partial provider names.</span></span>
<span data-ttu-id="656aa-130">Scheid meerdere provider namen met komma's.</span><span class="sxs-lookup"><span data-stu-id="656aa-130">Separate multiple provider names with commas.</span></span>
<span data-ttu-id="656aa-131">Geldige waarden voor deze para meter zijn namen van providers die u hebt geïnstalleerd met pakketten. Package Management wordt geleverd met een set standaard providers, met inbegrip van de **PSModule** -en **MSI** -providers.</span><span class="sxs-lookup"><span data-stu-id="656aa-131">Valid values for this parameter include names of providers that you have installed with packages; PackageManagement ships with a set of default providers, including the **PSModule** and **MSI** providers.</span></span>

```yaml
Type: System.String[]
Parameter Sets: (All)
Aliases:

Required: False
Position: 0
Default value: None
Accept pipeline input: False
Accept wildcard characters: False
```

### <span data-ttu-id="656aa-132">CommonParameters</span><span class="sxs-lookup"><span data-stu-id="656aa-132">CommonParameters</span></span>

<span data-ttu-id="656aa-133">Deze cmdlet biedt ondersteuning voor de meest gebruikte parameters: -Debug, - ErrorAction, - ErrorVariable, - InformationAction, -InformationVariable, - OutVariable,-OutBuffer, - PipelineVariable - Verbose, - WarningAction en -WarningVariable.</span><span class="sxs-lookup"><span data-stu-id="656aa-133">This cmdlet supports the common parameters: -Debug, -ErrorAction, -ErrorVariable, -InformationAction, -InformationVariable, -OutVariable, -OutBuffer, -PipelineVariable, -Verbose, -WarningAction, and -WarningVariable.</span></span> <span data-ttu-id="656aa-134">Zie [about_CommonParameters](https://go.microsoft.com/fwlink/?LinkID=113216)voor meer informatie.</span><span class="sxs-lookup"><span data-stu-id="656aa-134">For more information, see [about_CommonParameters](https://go.microsoft.com/fwlink/?LinkID=113216).</span></span>

## <span data-ttu-id="656aa-135">INVOER</span><span class="sxs-lookup"><span data-stu-id="656aa-135">INPUTS</span></span>

## <span data-ttu-id="656aa-136">UITVOER</span><span class="sxs-lookup"><span data-stu-id="656aa-136">OUTPUTS</span></span>

### <span data-ttu-id="656aa-137">Package provider []</span><span class="sxs-lookup"><span data-stu-id="656aa-137">PackageProvider[]</span></span>

## <span data-ttu-id="656aa-138">OPMERKINGEN</span><span class="sxs-lookup"><span data-stu-id="656aa-138">NOTES</span></span>

> [!IMPORTANT]
> <span data-ttu-id="656aa-139">Vanaf april 2020 biedt de PowerShell Gallery niet langer ondersteuning voor Transport Layer Security (TLS) versie 1,0 en 1,1.</span><span class="sxs-lookup"><span data-stu-id="656aa-139">As of April 2020, the PowerShell Gallery no longer supports Transport Layer Security (TLS) versions 1.0 and 1.1.</span></span> <span data-ttu-id="656aa-140">Als u geen TLS 1,2 of hoger gebruikt, wordt er een fout bericht weer gegeven wanneer u probeert toegang te krijgen tot de PowerShell Gallery.</span><span class="sxs-lookup"><span data-stu-id="656aa-140">If you are not using TLS 1.2 or higher, you will receive an error when trying to access the PowerShell Gallery.</span></span> <span data-ttu-id="656aa-141">Gebruik de volgende opdracht om ervoor te zorgen dat u TLS 1,2 gebruikt:</span><span class="sxs-lookup"><span data-stu-id="656aa-141">Use the following command to ensure you are using TLS 1.2:</span></span>
>
> `[Net.ServicePointManager]::SecurityProtocol = [Net.SecurityProtocolType]::Tls12`
>
> <span data-ttu-id="656aa-142">Zie de [aankondiging](https://devblogs.microsoft.com/powershell/powershell-gallery-tls-support/) in het Power shell-blog voor meer informatie.</span><span class="sxs-lookup"><span data-stu-id="656aa-142">For more information, see the [announcement](https://devblogs.microsoft.com/powershell/powershell-gallery-tls-support/) in the PowerShell blog.</span></span>

## <span data-ttu-id="656aa-143">GERELATEERDE KOPPELINGEN</span><span class="sxs-lookup"><span data-stu-id="656aa-143">RELATED LINKS</span></span>

[<span data-ttu-id="656aa-144">about_PackageManagement</span><span class="sxs-lookup"><span data-stu-id="656aa-144">about_PackageManagement</span></span>](../Microsoft.PowerShell.Core/About/about_PackageManagement.md)

[<span data-ttu-id="656aa-145">Get-PackageSource</span><span class="sxs-lookup"><span data-stu-id="656aa-145">Get-PackageSource</span></span>](Get-PackageSource.md)

[<span data-ttu-id="656aa-146">REGI ster-PackageSource</span><span class="sxs-lookup"><span data-stu-id="656aa-146">Register-PackageSource</span></span>](Register-PackageSource.md)

[<span data-ttu-id="656aa-147">Registratie ongedaan maken-PackageSource</span><span class="sxs-lookup"><span data-stu-id="656aa-147">Unregister-PackageSource</span></span>](Unregister-PackageSource.md)
