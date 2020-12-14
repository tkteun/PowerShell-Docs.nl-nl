---
external help file: Microsoft.PowerShell.PackageManagement.dll-Help.xml
Locale: en-US
Module Name: PackageManagement
ms.date: 06/09/2017
online version: https://docs.microsoft.com/powershell/module/packagemanagement/import-packageprovider?view=powershell-7.2&WT.mc_id=ps-gethelp
schema: 2.0.0
title: Import-PackageProvider
ms.openlocfilehash: 6c19d1cbc7b7e4dc37e24c466f83efae688f3cec
ms.sourcegitcommit: 22c93550c87af30c4895fcb9e9dd65e30d60ada0
ms.translationtype: MT
ms.contentlocale: nl-NL
ms.lasthandoff: 11/19/2020
ms.locfileid: "94889473"
---
# <span data-ttu-id="9a092-102">Import-PackageProvider</span><span class="sxs-lookup"><span data-stu-id="9a092-102">Import-PackageProvider</span></span>

## <span data-ttu-id="9a092-103">SAMENVATTING</span><span class="sxs-lookup"><span data-stu-id="9a092-103">SYNOPSIS</span></span>
<span data-ttu-id="9a092-104">Voegt pakket beheer pakket providers toe aan de huidige sessie.</span><span class="sxs-lookup"><span data-stu-id="9a092-104">Adds Package Management package providers to the current session.</span></span>

## <span data-ttu-id="9a092-105">SYNTAXIS</span><span class="sxs-lookup"><span data-stu-id="9a092-105">SYNTAX</span></span>

```
Import-PackageProvider [-Name] <String[]> [-RequiredVersion <String>] [-MinimumVersion <String>]
 [-MaximumVersion <String>] [-Force] [-ForceBootstrap] [<CommonParameters>]
```

## <span data-ttu-id="9a092-106">BESCHRIJVING</span><span class="sxs-lookup"><span data-stu-id="9a092-106">DESCRIPTION</span></span>

<span data-ttu-id="9a092-107">De `Import-PackageProvider` cmdlet voegt een of meer pakket providers toe aan de huidige sessie.</span><span class="sxs-lookup"><span data-stu-id="9a092-107">The `Import-PackageProvider` cmdlet adds one or more package providers to the current session.</span></span>
<span data-ttu-id="9a092-108">De provider die u importeert, moet op de lokale computer zijn geïnstalleerd.</span><span class="sxs-lookup"><span data-stu-id="9a092-108">The provider that you import must be installed on the local computer.</span></span>

<span data-ttu-id="9a092-109">Voer uit om een lijst met beschik bare providers te verkrijgen `Get-PackageProvider -ListAvailable` .</span><span class="sxs-lookup"><span data-stu-id="9a092-109">To get a list of available providers, run `Get-PackageProvider -ListAvailable`.</span></span>
<span data-ttu-id="9a092-110">Houd er rekening mee dat de naam van een pakket provider kan afwijken van de module naam.</span><span class="sxs-lookup"><span data-stu-id="9a092-110">Note that a package provider name can be different from its module name.</span></span>

<span data-ttu-id="9a092-111">Om veiligheids redenen vereist **Package Management** dat C#-providers een bevatten `provider.manifest` .</span><span class="sxs-lookup"><span data-stu-id="9a092-111">Due to security reasons, **PackageManagement** requires C#-based providers to contain a `provider.manifest`.</span></span> <span data-ttu-id="9a092-112">`provider.manifest`Zie de `.csproj` Project bestanden op voor meer informatie over het bouwen van een provider met injected [https://github.com/oneget/oneget](https://github.com/oneget/oneget) .</span><span class="sxs-lookup"><span data-stu-id="9a092-112">For more information on how to build a provider with `provider.manifest` injected, see the `.csproj` project files on [https://github.com/oneget/oneget](https://github.com/oneget/oneget).</span></span>

## <span data-ttu-id="9a092-113">VOORBEELDEN</span><span class="sxs-lookup"><span data-stu-id="9a092-113">EXAMPLES</span></span>

### <span data-ttu-id="9a092-114">Voor beeld 1: een pakket provider importeren van de lokale computer</span><span class="sxs-lookup"><span data-stu-id="9a092-114">Example 1: Import a package provider from the local computer</span></span>

```powershell
PS C:\> Import-PackageProvider -Name "Nuget"
```

<span data-ttu-id="9a092-115">Met deze opdracht wordt de Nuget-provider geïmporteerd nadat deze is geïnstalleerd op de lokale computer.</span><span class="sxs-lookup"><span data-stu-id="9a092-115">This command imports the Nuget provider after it has been installed on the local computer.</span></span>

### <span data-ttu-id="9a092-116">Voor beeld 2: een specifieke versie van een pakket provider importeren</span><span class="sxs-lookup"><span data-stu-id="9a092-116">Example 2: Import a specific version of a package provider</span></span>

```powershell
PS C:\> Find-PackageProvider -Name "Nuget" -AllVersions
Install-PackageProvider -Name "Nuget" -RequiredVersion "2.8.5.201" -Force
Get-PackageProvider -ListAvailable
Import-PackageProvider -Name "Nuget" -RequiredVersion "2.8.5.201" -Verbose
```

<span data-ttu-id="9a092-117">Met deze opdracht wordt een specifieke versie van de Nuget-pakket provider gevonden, geïnstalleerd en geïmporteerd.</span><span class="sxs-lookup"><span data-stu-id="9a092-117">This command finds, installs, and imports a specific version of the Nuget package provider.</span></span>

## <span data-ttu-id="9a092-118">PARAMETERS</span><span class="sxs-lookup"><span data-stu-id="9a092-118">PARAMETERS</span></span>

### <span data-ttu-id="9a092-119">-Force</span><span class="sxs-lookup"><span data-stu-id="9a092-119">-Force</span></span>

<span data-ttu-id="9a092-120">Hiermee wordt de opdracht uitgevoerd zonder dat de gebruiker om bevestiging wordt gevraagd.</span><span class="sxs-lookup"><span data-stu-id="9a092-120">Forces the command to run without asking for user confirmation.</span></span>
<span data-ttu-id="9a092-121">Hiermee wordt een pakket provider opnieuw geïmporteerd.</span><span class="sxs-lookup"><span data-stu-id="9a092-121">Re-imports a package provider.</span></span>

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

### <span data-ttu-id="9a092-122">-ForceBootstrap</span><span class="sxs-lookup"><span data-stu-id="9a092-122">-ForceBootstrap</span></span>

<span data-ttu-id="9a092-123">Geeft aan dat deze cmdlet pakket beheer afdwingt om de pakket provider automatisch te installeren.</span><span class="sxs-lookup"><span data-stu-id="9a092-123">Indicates that this cmdlet forces Package Management to automatically install the package provider.</span></span>

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

### <span data-ttu-id="9a092-124">-MaximumVersion</span><span class="sxs-lookup"><span data-stu-id="9a092-124">-MaximumVersion</span></span>

<span data-ttu-id="9a092-125">Hiermee geeft u de Maxi maal toegestane versie van de pakket provider die u wilt importeren.</span><span class="sxs-lookup"><span data-stu-id="9a092-125">Specifies the maximum allowed version of the package provider that you want to import.</span></span> <span data-ttu-id="9a092-126">Als u deze para meter niet toevoegt, wordt `Import-PackageProvider` de hoogste beschik bare versie van de provider geïmporteerd.</span><span class="sxs-lookup"><span data-stu-id="9a092-126">If you do not add this parameter, `Import-PackageProvider` imports the highest available version of the provider.</span></span>

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

### <span data-ttu-id="9a092-127">-MinimumVersion</span><span class="sxs-lookup"><span data-stu-id="9a092-127">-MinimumVersion</span></span>

<span data-ttu-id="9a092-128">Hiermee geeft u de mini maal toegestane versie van de pakket provider die u wilt importeren.</span><span class="sxs-lookup"><span data-stu-id="9a092-128">Specifies the minimum allowed version of the package provider that you want to import.</span></span> <span data-ttu-id="9a092-129">Als u deze para meter niet toevoegt, wordt `Import-PackageProvider` de hoogste beschik bare versie van het pakket geïmporteerd die ook voldoet aan de maximum versie die is opgegeven met behulp van de para meter *MaximumVersion* .</span><span class="sxs-lookup"><span data-stu-id="9a092-129">If you do not add this parameter, `Import-PackageProvider` imports the highest available version of the package that also satisfies any maximum version that is specified using the *MaximumVersion* parameter.</span></span>

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

### <span data-ttu-id="9a092-130">-Name</span><span class="sxs-lookup"><span data-stu-id="9a092-130">-Name</span></span>

<span data-ttu-id="9a092-131">Hiermee geeft u een of meer pakket provider namen op.</span><span class="sxs-lookup"><span data-stu-id="9a092-131">Specifies one or more package provider names.</span></span> <span data-ttu-id="9a092-132">Joker tekens zijn niet toegestaan.</span><span class="sxs-lookup"><span data-stu-id="9a092-132">Wildcards are not permitted.</span></span>

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

### <span data-ttu-id="9a092-133">-RequiredVersion</span><span class="sxs-lookup"><span data-stu-id="9a092-133">-RequiredVersion</span></span>

<span data-ttu-id="9a092-134">Hiermee geeft u de exacte versie van de pakket provider die u wilt importeren.</span><span class="sxs-lookup"><span data-stu-id="9a092-134">Specifies the exact version of the package provider that you want to import.</span></span> <span data-ttu-id="9a092-135">Als u deze para meter niet toevoegt, wordt `Import-PackageProvider` de hoogste beschik bare versie van de provider geïmporteerd die ook voldoet aan de maximum versie die is opgegeven met behulp van de para meter **MaximumVersion** .</span><span class="sxs-lookup"><span data-stu-id="9a092-135">If you do not add this parameter, `Import-PackageProvider` imports the highest available version of the provider that also satisfies any maximum version specified using the **MaximumVersion** parameter.</span></span>

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

### <span data-ttu-id="9a092-136">CommonParameters</span><span class="sxs-lookup"><span data-stu-id="9a092-136">CommonParameters</span></span>

<span data-ttu-id="9a092-137">Deze cmdlet biedt ondersteuning voor de meest gebruikte parameters: -Debug, - ErrorAction, - ErrorVariable, - InformationAction, -InformationVariable, - OutVariable,-OutBuffer, - PipelineVariable - Verbose, - WarningAction en -WarningVariable.</span><span class="sxs-lookup"><span data-stu-id="9a092-137">This cmdlet supports the common parameters: -Debug, -ErrorAction, -ErrorVariable, -InformationAction, -InformationVariable, -OutVariable, -OutBuffer, -PipelineVariable, -Verbose, -WarningAction, and -WarningVariable.</span></span> <span data-ttu-id="9a092-138">Zie [about_CommonParameters](https://go.microsoft.com/fwlink/?LinkID=113216)voor meer informatie.</span><span class="sxs-lookup"><span data-stu-id="9a092-138">For more information, see [about_CommonParameters](https://go.microsoft.com/fwlink/?LinkID=113216).</span></span>

## <span data-ttu-id="9a092-139">INVOER</span><span class="sxs-lookup"><span data-stu-id="9a092-139">INPUTS</span></span>

### <span data-ttu-id="9a092-140">Micro soft. package management. Implementation. package provider</span><span class="sxs-lookup"><span data-stu-id="9a092-140">Microsoft.PackageManagement.Implementation.PackageProvider</span></span>

<span data-ttu-id="9a092-141">U kunt een **package provider** -object dat wordt geretourneerd door `Get-PackageProvider` in `Import-PackageProvider` .</span><span class="sxs-lookup"><span data-stu-id="9a092-141">You can pipe a **PackageProvider** object returned by `Get-PackageProvider` into `Import-PackageProvider`.</span></span>

## <span data-ttu-id="9a092-142">UITVOER</span><span class="sxs-lookup"><span data-stu-id="9a092-142">OUTPUTS</span></span>

## <span data-ttu-id="9a092-143">OPMERKINGEN</span><span class="sxs-lookup"><span data-stu-id="9a092-143">NOTES</span></span>

> [!IMPORTANT]
> <span data-ttu-id="9a092-144">Vanaf april 2020 biedt de PowerShell Gallery niet langer ondersteuning voor Transport Layer Security (TLS) versie 1,0 en 1,1.</span><span class="sxs-lookup"><span data-stu-id="9a092-144">As of April 2020, the PowerShell Gallery no longer supports Transport Layer Security (TLS) versions 1.0 and 1.1.</span></span> <span data-ttu-id="9a092-145">Als u geen TLS 1,2 of hoger gebruikt, wordt er een fout bericht weer gegeven wanneer u probeert toegang te krijgen tot de PowerShell Gallery.</span><span class="sxs-lookup"><span data-stu-id="9a092-145">If you are not using TLS 1.2 or higher, you will receive an error when trying to access the PowerShell Gallery.</span></span> <span data-ttu-id="9a092-146">Gebruik de volgende opdracht om ervoor te zorgen dat u TLS 1,2 gebruikt:</span><span class="sxs-lookup"><span data-stu-id="9a092-146">Use the following command to ensure you are using TLS 1.2:</span></span>
>
> `[Net.ServicePointManager]::SecurityProtocol = [Net.SecurityProtocolType]::Tls12`
>
> <span data-ttu-id="9a092-147">Zie de [aankondiging](https://devblogs.microsoft.com/powershell/powershell-gallery-tls-support/) in het Power shell-blog voor meer informatie.</span><span class="sxs-lookup"><span data-stu-id="9a092-147">For more information, see the [announcement](https://devblogs.microsoft.com/powershell/powershell-gallery-tls-support/) in the PowerShell blog.</span></span>

## <span data-ttu-id="9a092-148">GERELATEERDE KOPPELINGEN</span><span class="sxs-lookup"><span data-stu-id="9a092-148">RELATED LINKS</span></span>

[<span data-ttu-id="9a092-149">about_PackageManagement</span><span class="sxs-lookup"><span data-stu-id="9a092-149">about_PackageManagement</span></span>](../Microsoft.PowerShell.Core/About/about_PackageManagement.md)

[<span data-ttu-id="9a092-150">Registratie ongedaan maken-PackageSource</span><span class="sxs-lookup"><span data-stu-id="9a092-150">Unregister-PackageSource</span></span>](Unregister-PackageSource.md)

[<span data-ttu-id="9a092-151">Get-PackageSource</span><span class="sxs-lookup"><span data-stu-id="9a092-151">Get-PackageSource</span></span>](Get-PackageSource.md)

[<span data-ttu-id="9a092-152">REGI ster-PackageSource</span><span class="sxs-lookup"><span data-stu-id="9a092-152">Register-PackageSource</span></span>](Register-PackageSource.md)

[<span data-ttu-id="9a092-153">Get-PackageProvider</span><span class="sxs-lookup"><span data-stu-id="9a092-153">Get-PackageProvider</span></span>](Get-PackageProvider.md)
