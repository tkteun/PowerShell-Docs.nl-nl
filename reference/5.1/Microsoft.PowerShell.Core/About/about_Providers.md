---
description: Hierin wordt beschreven hoe Power shell-providers toegang bieden tot gegevens en onderdelen die anders niet eenvoudig toegankelijk zijn via de opdracht regel. De gegevens worden weer gegeven in een consistente indeling die lijkt op een bestandssysteem station.
keywords: powershell,cmdlet
Locale: en-US
ms.date: 03/27/2020
online version: https://docs.microsoft.com/powershell/module/microsoft.powershell.core/about/about_providers?view=powershell-5.1&WT.mc_id=ps-gethelp
schema: 2.0.0
title: about_Providers
ms.openlocfilehash: 952ab618f1e47f0f912209ba56c37a667c596aaf
ms.sourcegitcommit: f874dc1d4236e06a3df195d179f59e0a7d9f8436
ms.translationtype: MT
ms.contentlocale: nl-NL
ms.lasthandoff: 10/13/2020
ms.locfileid: "93252583"
---
# <a name="about-providers"></a><span data-ttu-id="accfb-105">Over providers</span><span class="sxs-lookup"><span data-stu-id="accfb-105">About Providers</span></span>

## <a name="short-description"></a><span data-ttu-id="accfb-106">Korte beschrijving</span><span class="sxs-lookup"><span data-stu-id="accfb-106">Short description</span></span>
<span data-ttu-id="accfb-107">Hierin wordt beschreven hoe Power shell-providers toegang bieden tot gegevens en onderdelen die anders niet eenvoudig toegankelijk zijn via de opdracht regel.</span><span class="sxs-lookup"><span data-stu-id="accfb-107">Describes how PowerShell providers provide access to data and components that wouldn't otherwise be easily accessible at the command line.</span></span>
<span data-ttu-id="accfb-108">De gegevens worden weer gegeven in een consistente indeling die lijkt op een bestandssysteem station.</span><span class="sxs-lookup"><span data-stu-id="accfb-108">The data is presented in a consistent format that resembles a file system drive.</span></span>

## <a name="long-description"></a><span data-ttu-id="accfb-109">Lange beschrijving</span><span class="sxs-lookup"><span data-stu-id="accfb-109">Long description</span></span>

<span data-ttu-id="accfb-110">Power shell-providers zijn .NET-Program ma's die toegang bieden tot gespecialiseerde gegevens archieven, zodat ze eenvoudiger kunnen worden bekeken en beheerd.</span><span class="sxs-lookup"><span data-stu-id="accfb-110">PowerShell providers are .NET programs that provide access to specialized data stores for easier viewing and management.</span></span> <span data-ttu-id="accfb-111">De gegevens worden weer gegeven in een station en u hebt toegang tot de gegevens in een pad zoals u zou doen op een harde schijf.</span><span class="sxs-lookup"><span data-stu-id="accfb-111">The data appears in a drive, and you access the data in a path like you would on a hard disk drive.</span></span> <span data-ttu-id="accfb-112">U kunt een van de ingebouwde cmdlets gebruiken die door de provider worden ondersteund voor het beheren van de gegevens in het provider station.</span><span class="sxs-lookup"><span data-stu-id="accfb-112">You can use any of the built-in cmdlets that the provider supports to manage the data in the provider drive.</span></span> <span data-ttu-id="accfb-113">En u kunt aangepaste cmdlets gebruiken die speciaal zijn ontworpen voor de gegevens.</span><span class="sxs-lookup"><span data-stu-id="accfb-113">And, you can use custom cmdlets that are designed especially for the data.</span></span>

<span data-ttu-id="accfb-114">De providers kunnen ook dynamische para meters toevoegen aan de ingebouwde cmdlets.</span><span class="sxs-lookup"><span data-stu-id="accfb-114">The providers can also add dynamic parameters to the built-in cmdlets.</span></span> <span data-ttu-id="accfb-115">Deze para meters zijn alleen beschikbaar wanneer u de cmdlet met de provider gegevens gebruikt.</span><span class="sxs-lookup"><span data-stu-id="accfb-115">These parameters are only available when you use the cmdlet with the provider data.</span></span>

## <a name="built-in-providers"></a><span data-ttu-id="accfb-116">Ingebouwde providers</span><span class="sxs-lookup"><span data-stu-id="accfb-116">Built-in providers</span></span>

<span data-ttu-id="accfb-117">Power shell bevat een set ingebouwde providers die u kunt gebruiken om toegang te krijgen tot de verschillende typen gegevens archieven.</span><span class="sxs-lookup"><span data-stu-id="accfb-117">PowerShell includes a set of built-in providers that you can use to access the different types of data stores.</span></span>

| <span data-ttu-id="accfb-118">Provider</span><span class="sxs-lookup"><span data-stu-id="accfb-118">Provider</span></span>   |   <span data-ttu-id="accfb-119">Station (s)</span><span class="sxs-lookup"><span data-stu-id="accfb-119">Drive(s)</span></span>  |<span data-ttu-id="accfb-120">Type</span><span class="sxs-lookup"><span data-stu-id="accfb-120">OutputType</span></span>                                                    |
|----------- |------------ |--------------------------------------------------------------|
|<span data-ttu-id="accfb-121">Alias</span><span class="sxs-lookup"><span data-stu-id="accfb-121">Alias</span></span>       |<span data-ttu-id="accfb-122">Toe</span><span class="sxs-lookup"><span data-stu-id="accfb-122">Alias:</span></span>       |<span data-ttu-id="accfb-123">System. Management. Automation. AliasInfo</span><span class="sxs-lookup"><span data-stu-id="accfb-123">System.Management.Automation.AliasInfo</span></span>                        |
|<span data-ttu-id="accfb-124">Certificaat</span><span class="sxs-lookup"><span data-stu-id="accfb-124">Certificate</span></span> |<span data-ttu-id="accfb-125">Certificaat</span><span class="sxs-lookup"><span data-stu-id="accfb-125">Cert:</span></span>        |<span data-ttu-id="accfb-126">Micro soft. Power shell. commands. X509StoreLocation</span><span class="sxs-lookup"><span data-stu-id="accfb-126">Microsoft.PowerShell.Commands.X509StoreLocation</span></span>               |
|            |             |<span data-ttu-id="accfb-127">System. Security. Cryptography. X509Certificates. X509Certificate2</span><span class="sxs-lookup"><span data-stu-id="accfb-127">System.Security.Cryptography.X509Certificates.X509Certificate2</span></span>|
|<span data-ttu-id="accfb-128">Omgeving</span><span class="sxs-lookup"><span data-stu-id="accfb-128">Environment</span></span> |<span data-ttu-id="accfb-129">Envelop</span><span class="sxs-lookup"><span data-stu-id="accfb-129">Env:</span></span>         |<span data-ttu-id="accfb-130">System. Collections. Dictionary entry</span><span class="sxs-lookup"><span data-stu-id="accfb-130">System.Collections.DictionaryEntry</span></span>                            |
|<span data-ttu-id="accfb-131">Bestandssysteem</span><span class="sxs-lookup"><span data-stu-id="accfb-131">FileSystem</span></span>  |<span data-ttu-id="accfb-132">C: (\*)</span><span class="sxs-lookup"><span data-stu-id="accfb-132">C: (\*)</span></span>       |<span data-ttu-id="accfb-133">System. IO. file info</span><span class="sxs-lookup"><span data-stu-id="accfb-133">System.IO.FileInfo</span></span>                                            |
|            |             |<span data-ttu-id="accfb-134">System. IO. DirectoryInfo</span><span class="sxs-lookup"><span data-stu-id="accfb-134">System.IO.DirectoryInfo</span></span>                                       |
|<span data-ttu-id="accfb-135">Functie</span><span class="sxs-lookup"><span data-stu-id="accfb-135">Function</span></span>    |<span data-ttu-id="accfb-136">Functieassembly</span><span class="sxs-lookup"><span data-stu-id="accfb-136">Function:</span></span>    |<span data-ttu-id="accfb-137">System. Management. Automation. FunctionInfo</span><span class="sxs-lookup"><span data-stu-id="accfb-137">System.Management.Automation.FunctionInfo</span></span>                     |
|<span data-ttu-id="accfb-138">Register</span><span class="sxs-lookup"><span data-stu-id="accfb-138">Registry</span></span>    |<span data-ttu-id="accfb-139">HKLM: HKCU:</span><span class="sxs-lookup"><span data-stu-id="accfb-139">HKLM: HKCU:</span></span>  |<span data-ttu-id="accfb-140">Microsoft. Win32. RegistryKey</span><span class="sxs-lookup"><span data-stu-id="accfb-140">Microsoft.Win32.RegistryKey</span></span>                                   |
|<span data-ttu-id="accfb-141">Variabele</span><span class="sxs-lookup"><span data-stu-id="accfb-141">Variable</span></span>    |<span data-ttu-id="accfb-142">Variabeletype</span><span class="sxs-lookup"><span data-stu-id="accfb-142">Variable:</span></span>    |<span data-ttu-id="accfb-143">System. Management. Automation. PSVariable</span><span class="sxs-lookup"><span data-stu-id="accfb-143">System.Management.Automation.PSVariable</span></span>                       |
|<span data-ttu-id="accfb-144">WSMan</span><span class="sxs-lookup"><span data-stu-id="accfb-144">WSMan</span></span>       |<span data-ttu-id="accfb-145">WSMan</span><span class="sxs-lookup"><span data-stu-id="accfb-145">WSMan:</span></span>       |<span data-ttu-id="accfb-146">Micro soft. WSMan. Management. WSManConfigContainerElement</span><span class="sxs-lookup"><span data-stu-id="accfb-146">Microsoft.WSMan.Management.WSManConfigContainerElement</span></span>        |

<span data-ttu-id="accfb-147">(\*) De stations van het bestands systeem variëren per systeem.</span><span class="sxs-lookup"><span data-stu-id="accfb-147">(\*) The FileSystem drives vary on each system.</span></span>

<span data-ttu-id="accfb-148">U kunt ook uw eigen Power shell-providers maken en u kunt providers installeren die anderen ontwikkelen.</span><span class="sxs-lookup"><span data-stu-id="accfb-148">You can also create your own PowerShell providers, and you can install providers that others develop.</span></span> <span data-ttu-id="accfb-149">Als u een lijst wilt weer geven van de providers die beschikbaar zijn in uw sessie, typt u:</span><span class="sxs-lookup"><span data-stu-id="accfb-149">To list the providers that are available in your session, type:</span></span>

```powershell
Get-PSProvider
```

## <a name="installing-and-removing-providers"></a><span data-ttu-id="accfb-150">Providers installeren en verwijderen</span><span class="sxs-lookup"><span data-stu-id="accfb-150">Installing and removing providers</span></span>

<span data-ttu-id="accfb-151">Providers worden doorgaans geïnstalleerd via Power shell-modules.</span><span class="sxs-lookup"><span data-stu-id="accfb-151">Providers are typically installed via PowerShell modules.</span></span> <span data-ttu-id="accfb-152">Als u de module importeert, wordt de provider in uw sessie geladen.</span><span class="sxs-lookup"><span data-stu-id="accfb-152">Importing the module loads the provider into your session.</span></span> <span data-ttu-id="accfb-153">U kunt de ingebouwde providers niet verwijderen.</span><span class="sxs-lookup"><span data-stu-id="accfb-153">You can't uninstall the built-in providers.</span></span> <span data-ttu-id="accfb-154">U kunt de door andere modules geladen providers verwijderen.</span><span class="sxs-lookup"><span data-stu-id="accfb-154">You can uninstall providers loaded by other modules.</span></span>

<span data-ttu-id="accfb-155">U kunt een provider uit de huidige sessie verwijderen met de `Remove-Module` cmdlet.</span><span class="sxs-lookup"><span data-stu-id="accfb-155">You can unload a provider from the current session using the `Remove-Module` cmdlet.</span></span> <span data-ttu-id="accfb-156">Met deze cmdlet wordt de provider niet verwijderd, maar wordt de provider niet beschikbaar in de sessie.</span><span class="sxs-lookup"><span data-stu-id="accfb-156">This cmdlet doesn't uninstall the provider, but it makes the provider unavailable in the session.</span></span>

<span data-ttu-id="accfb-157">U kunt ook de `Remove-PSDrive` cmdlet gebruiken om een station uit de huidige sessie te verwijderen.</span><span class="sxs-lookup"><span data-stu-id="accfb-157">You can also use the `Remove-PSDrive` cmdlet to remove any drive from the current session.</span></span> <span data-ttu-id="accfb-158">Deze gegevens op het station worden niet beïnvloed, maar het station is niet meer beschikbaar in die sessie.</span><span class="sxs-lookup"><span data-stu-id="accfb-158">This data on the drive isn't affected, but the drive is no longer available in that session.</span></span>

## <a name="viewing-providers"></a><span data-ttu-id="accfb-159">Providers weer geven</span><span class="sxs-lookup"><span data-stu-id="accfb-159">Viewing providers</span></span>

<span data-ttu-id="accfb-160">Als u de Power shell-providers op uw computer wilt weer geven, typt u:</span><span class="sxs-lookup"><span data-stu-id="accfb-160">To view the PowerShell providers on your computer, type:</span></span>

```powershell
Get-PSProvider
```

<span data-ttu-id="accfb-161">De uitvoer bevat een lijst met de ingebouwde providers en de providers die u hebt toegevoegd aan de sessie.</span><span class="sxs-lookup"><span data-stu-id="accfb-161">The output lists the built-in providers and the providers that you added to the session.</span></span>

## <a name="the-provider-cmdlets"></a><span data-ttu-id="accfb-162">De provider-cmdlets</span><span class="sxs-lookup"><span data-stu-id="accfb-162">The provider cmdlets</span></span>

<span data-ttu-id="accfb-163">De volgende cmdlets zijn ontworpen om te werken met de gegevens die door elke provider worden weer gegeven.</span><span class="sxs-lookup"><span data-stu-id="accfb-163">The following cmdlets are designed to work with the data exposed by any provider.</span></span> <span data-ttu-id="accfb-164">U kunt dezelfde cmdlets op dezelfde manier gebruiken voor het beheren van de verschillende typen gegevens die providers beschikbaar maken.</span><span class="sxs-lookup"><span data-stu-id="accfb-164">You can use the same cmdlets in the same way to manage the different types of data that providers expose.</span></span> <span data-ttu-id="accfb-165">Wanneer u de gegevens van een provider hebt beheerd, kunt u dezelfde procedures gebruiken met de gegevens van een provider.</span><span class="sxs-lookup"><span data-stu-id="accfb-165">After you learn to manage the data of one provider, you can use the same procedures with the data from any provider.</span></span>

<span data-ttu-id="accfb-166">Met de `New-Item` cmdlet maakt u bijvoorbeeld een nieuw item.</span><span class="sxs-lookup"><span data-stu-id="accfb-166">For example, the `New-Item` cmdlet creates a new item.</span></span> <span data-ttu-id="accfb-167">In het `C:` station dat door de **File System** provider wordt ondersteund, kunt u gebruiken `New-Item` om een nieuw bestand of nieuwe map te maken.</span><span class="sxs-lookup"><span data-stu-id="accfb-167">In the `C:` drive that is supported by the **FileSystem** provider, you can use `New-Item` to create a new file or folder.</span></span> <span data-ttu-id="accfb-168">In de stations die worden ondersteund door de **register** provider, kunt u gebruiken `New-Item` om een nieuwe register sleutel te maken.</span><span class="sxs-lookup"><span data-stu-id="accfb-168">In the drives that are supported by the **Registry** provider, you can use `New-Item` to create a new registry key.</span></span> <span data-ttu-id="accfb-169">In het `Alias:` station kunt u gebruiken `New-Item` om een nieuwe alias te maken.</span><span class="sxs-lookup"><span data-stu-id="accfb-169">In the `Alias:` drive, you can use `New-Item` to create a new alias.</span></span>

<span data-ttu-id="accfb-170">Voor gedetailleerde informatie over een van de volgende cmdlets, typt u:</span><span class="sxs-lookup"><span data-stu-id="accfb-170">For detailed information about any of the following cmdlets, type:</span></span>

```
Get-Help <cmdlet-name> -Detailed
```

### <a name="childitem-cmdlets"></a><span data-ttu-id="accfb-171">Child item-cmdlets</span><span class="sxs-lookup"><span data-stu-id="accfb-171">ChildItem cmdlets</span></span>

- [<span data-ttu-id="accfb-172">Get-Child item</span><span class="sxs-lookup"><span data-stu-id="accfb-172">Get-ChildItem</span></span>](xref:Microsoft.PowerShell.Management.Get-ChildItem)

### <a name="content-cmdlets"></a><span data-ttu-id="accfb-173">Cmdlets voor inhoud</span><span class="sxs-lookup"><span data-stu-id="accfb-173">Content Cmdlets</span></span>

- [<span data-ttu-id="accfb-174">Add-content</span><span class="sxs-lookup"><span data-stu-id="accfb-174">Add-Content</span></span>](xref:Microsoft.PowerShell.Management.Add-Content)
- [<span data-ttu-id="accfb-175">Wissen-inhoud</span><span class="sxs-lookup"><span data-stu-id="accfb-175">Clear-Content</span></span>](xref:Microsoft.PowerShell.Management.Clear-Content)
- [<span data-ttu-id="accfb-176">Get-Content</span><span class="sxs-lookup"><span data-stu-id="accfb-176">Get-Content</span></span>](xref:Microsoft.PowerShell.Management.Get-Content)
- [<span data-ttu-id="accfb-177">Set-Content</span><span class="sxs-lookup"><span data-stu-id="accfb-177">Set-Content</span></span>](xref:Microsoft.PowerShell.Management.Set-Content)

### <a name="item-cmdlets"></a><span data-ttu-id="accfb-178">Cmdlets voor items</span><span class="sxs-lookup"><span data-stu-id="accfb-178">Item Cmdlets</span></span>

- [<span data-ttu-id="accfb-179">Wissen-item</span><span class="sxs-lookup"><span data-stu-id="accfb-179">Clear-Item</span></span>](xref:Microsoft.PowerShell.Management.Clear-Item)
- [<span data-ttu-id="accfb-180">Kopie-item</span><span class="sxs-lookup"><span data-stu-id="accfb-180">Copy-Item</span></span>](xref:Microsoft.PowerShell.Management.Copy-Item)
- [<span data-ttu-id="accfb-181">Get-item</span><span class="sxs-lookup"><span data-stu-id="accfb-181">Get-Item</span></span>](xref:Microsoft.PowerShell.Management.Get-Item)
- [<span data-ttu-id="accfb-182">Invoke-item</span><span class="sxs-lookup"><span data-stu-id="accfb-182">Invoke-Item</span></span>](xref:Microsoft.PowerShell.Management.Invoke-Item)
- [<span data-ttu-id="accfb-183">Item verplaatsen</span><span class="sxs-lookup"><span data-stu-id="accfb-183">Move-Item</span></span>](xref:Microsoft.PowerShell.Management.Move-Item)
- [<span data-ttu-id="accfb-184">Nieuw-item</span><span class="sxs-lookup"><span data-stu-id="accfb-184">New-Item</span></span>](xref:Microsoft.PowerShell.Management.New-Item)
- [<span data-ttu-id="accfb-185">Verwijderen-item</span><span class="sxs-lookup"><span data-stu-id="accfb-185">Remove-Item</span></span>](xref:Microsoft.PowerShell.Management.Remove-Item)
- [<span data-ttu-id="accfb-186">Naam wijzigen-item</span><span class="sxs-lookup"><span data-stu-id="accfb-186">Rename-Item</span></span>](xref:Microsoft.PowerShell.Management.Rename-Item)
- [<span data-ttu-id="accfb-187">Set-item</span><span class="sxs-lookup"><span data-stu-id="accfb-187">Set-Item</span></span>](xref:Microsoft.PowerShell.Management.Set-Item)

### <a name="itemproperty-cmdlets"></a><span data-ttu-id="accfb-188">Item Property-cmdlets</span><span class="sxs-lookup"><span data-stu-id="accfb-188">ItemProperty cmdlets</span></span>

- [<span data-ttu-id="accfb-189">Wissen-item Property</span><span class="sxs-lookup"><span data-stu-id="accfb-189">Clear-ItemProperty</span></span>](xref:Microsoft.PowerShell.Management.Clear-ItemProperty)
- [<span data-ttu-id="accfb-190">Kopiëren-item Property</span><span class="sxs-lookup"><span data-stu-id="accfb-190">Copy-ItemProperty</span></span>](xref:Microsoft.PowerShell.Management.Copy-ItemProperty)
- [<span data-ttu-id="accfb-191">Get-item Property</span><span class="sxs-lookup"><span data-stu-id="accfb-191">Get-ItemProperty</span></span>](xref:Microsoft.PowerShell.Management.Get-ItemProperty)
- [<span data-ttu-id="accfb-192">Verplaatsen-item Property</span><span class="sxs-lookup"><span data-stu-id="accfb-192">Move-ItemProperty</span></span>](xref:Microsoft.PowerShell.Management.Move-ItemProperty)
- [<span data-ttu-id="accfb-193">Nieuw-item Property</span><span class="sxs-lookup"><span data-stu-id="accfb-193">New-ItemProperty</span></span>](xref:Microsoft.PowerShell.Management.New-ItemProperty)
- [<span data-ttu-id="accfb-194">Verwijderen-item Property</span><span class="sxs-lookup"><span data-stu-id="accfb-194">Remove-ItemProperty</span></span>](xref:Microsoft.PowerShell.Management.Remove-ItemProperty)
- [<span data-ttu-id="accfb-195">Naam wijzigen-item Property</span><span class="sxs-lookup"><span data-stu-id="accfb-195">Rename-ItemProperty</span></span>](xref:Microsoft.PowerShell.Management.Rename-ItemProperty)
- [<span data-ttu-id="accfb-196">Set-item Property</span><span class="sxs-lookup"><span data-stu-id="accfb-196">Set-ItemProperty</span></span>](xref:Microsoft.PowerShell.Management.Set-ItemProperty)

### <a name="location-cmdlets"></a><span data-ttu-id="accfb-197">Locatie-cmdlets</span><span class="sxs-lookup"><span data-stu-id="accfb-197">Location cmdlets</span></span>

- [<span data-ttu-id="accfb-198">Get-locatie</span><span class="sxs-lookup"><span data-stu-id="accfb-198">Get-Location</span></span>](xref:Microsoft.PowerShell.Management.Get-Location)
- [<span data-ttu-id="accfb-199">Pop-locatie</span><span class="sxs-lookup"><span data-stu-id="accfb-199">Pop-Location</span></span>](xref:Microsoft.PowerShell.Management.Pop-Location)
- [<span data-ttu-id="accfb-200">Push-locatie</span><span class="sxs-lookup"><span data-stu-id="accfb-200">Push-Location</span></span>](xref:Microsoft.PowerShell.Management.Push-Location)
- [<span data-ttu-id="accfb-201">Set-Location</span><span class="sxs-lookup"><span data-stu-id="accfb-201">Set-Location</span></span>](xref:Microsoft.PowerShell.Management.Set-Location)

### <a name="path-cmdlets"></a><span data-ttu-id="accfb-202">Pad-cmdlets</span><span class="sxs-lookup"><span data-stu-id="accfb-202">Path cmdlets</span></span>

- [<span data-ttu-id="accfb-203">Pad voor samen voegen</span><span class="sxs-lookup"><span data-stu-id="accfb-203">Join-Path</span></span>](xref:Microsoft.PowerShell.Management.Join-Path)
- [<span data-ttu-id="accfb-204">Convert-pad</span><span class="sxs-lookup"><span data-stu-id="accfb-204">Convert-Path</span></span>](xref:Microsoft.PowerShell.Management.Convert-Path)
- [<span data-ttu-id="accfb-205">Split-pad</span><span class="sxs-lookup"><span data-stu-id="accfb-205">Split-Path</span></span>](xref:Microsoft.PowerShell.Management.Split-Path)
- [<span data-ttu-id="accfb-206">Oplossen-pad</span><span class="sxs-lookup"><span data-stu-id="accfb-206">Resolve-Path</span></span>](xref:Microsoft.PowerShell.Management.Resolve-Path)
- [<span data-ttu-id="accfb-207">Test-pad</span><span class="sxs-lookup"><span data-stu-id="accfb-207">Test-Path</span></span>](xref:Microsoft.PowerShell.Management.Test-Path)

### <a name="psdrive-cmdlets"></a><span data-ttu-id="accfb-208">PSDrive-cmdlets</span><span class="sxs-lookup"><span data-stu-id="accfb-208">PSDrive cmdlets</span></span>

- [<span data-ttu-id="accfb-209">Get-PSDrive</span><span class="sxs-lookup"><span data-stu-id="accfb-209">Get-PSDrive</span></span>](xref:Microsoft.PowerShell.Management.Get-PSDrive)
- [<span data-ttu-id="accfb-210">New-PSDrive</span><span class="sxs-lookup"><span data-stu-id="accfb-210">New-PSDrive</span></span>](xref:Microsoft.PowerShell.Management.New-PSDrive)
- [<span data-ttu-id="accfb-211">Remove-PSDrive</span><span class="sxs-lookup"><span data-stu-id="accfb-211">Remove-PSDrive</span></span>](xref:Microsoft.PowerShell.Management.Remove-PSDrive)

### <a name="psprovider-cmdlets"></a><span data-ttu-id="accfb-212">PSProvider-cmdlets</span><span class="sxs-lookup"><span data-stu-id="accfb-212">PSProvider Cmdlets</span></span>

- [<span data-ttu-id="accfb-213">Get-PSProvider</span><span class="sxs-lookup"><span data-stu-id="accfb-213">Get-PSProvider</span></span>](xref:Microsoft.PowerShell.Management.Get-PSProvider)

## <a name="viewing-provider-data"></a><span data-ttu-id="accfb-214">Provider gegevens weer geven</span><span class="sxs-lookup"><span data-stu-id="accfb-214">Viewing provider data</span></span>

<span data-ttu-id="accfb-215">Het belangrijkste voor deel van een provider is dat de gegevens op een vertrouwde en consistente manier beschikbaar worden gesteld.</span><span class="sxs-lookup"><span data-stu-id="accfb-215">The primary benefit of a provider is that it exposes its data in a familiar and consistent way.</span></span> <span data-ttu-id="accfb-216">Het model voor gegevens presentatie is een bestandssysteem station.</span><span class="sxs-lookup"><span data-stu-id="accfb-216">The model for data presentation is a file system drive.</span></span>

<span data-ttu-id="accfb-217">Met de provider kunt u items in het gegevens archief weer geven, navigeren en wijzigen, alsof deze gegevens in een bestands systeem waren.</span><span class="sxs-lookup"><span data-stu-id="accfb-217">The provider allows you to view, navigate, and change items in the data store as though they were data in a file system.</span></span> <span data-ttu-id="accfb-218">Het gegevens archief wordt geopend met de naam van het station dat wordt ondersteund.</span><span class="sxs-lookup"><span data-stu-id="accfb-218">The data store is accessed by the name of the drive that it supports.</span></span>

<span data-ttu-id="accfb-219">Het station wordt weer gegeven in de standaard weergave van de `Get-PSProvider` cmdlet, maar u kunt informatie over het provider station verkrijgen met de `Get-PSDrive` cmdlet.</span><span class="sxs-lookup"><span data-stu-id="accfb-219">The drive is listed in the default display of the `Get-PSProvider` cmdlet, but you can get information about the provider drive using the `Get-PSDrive` cmdlet.</span></span> <span data-ttu-id="accfb-220">Als u bijvoorbeeld alle eigenschappen van de functie wilt ophalen: station, typt u:</span><span class="sxs-lookup"><span data-stu-id="accfb-220">For example, to get all the properties of the Function: drive, type:</span></span>

```powershell
Get-PSDrive Function | Format-List *
```

<span data-ttu-id="accfb-221">U kunt de gegevens in een provider station bekijken en verplaatsen op dezelfde manier als op een bestandssysteem station.</span><span class="sxs-lookup"><span data-stu-id="accfb-221">You can view and move through the data in a provider drive just as you would on a file system drive.</span></span>

<span data-ttu-id="accfb-222">Als u de inhoud van een provider station wilt weer geven, gebruikt u de Get-Item-of Get-ChildItem-cmdlets.</span><span class="sxs-lookup"><span data-stu-id="accfb-222">To view the contents of a provider drive, use the Get-Item or Get-ChildItem cmdlets.</span></span> <span data-ttu-id="accfb-223">Typ de naam van het station gevolgd door een dubbele punt (:).</span><span class="sxs-lookup"><span data-stu-id="accfb-223">Type the drive name followed by a colon (:).</span></span> <span data-ttu-id="accfb-224">Als u bijvoorbeeld de inhoud van de alias wilt bekijken: station, typt u:</span><span class="sxs-lookup"><span data-stu-id="accfb-224">For example, to view the contents of the Alias: drive, type:</span></span>

```powershell
Get-Item alias:
```

<span data-ttu-id="accfb-225">U kunt de gegevens in een wille keurig station weer geven en beheren vanaf een ander station door de naam van het station in het pad op te nemen.</span><span class="sxs-lookup"><span data-stu-id="accfb-225">You can view and manage the data in any drive from another drive by including the drive name in the path.</span></span> <span data-ttu-id="accfb-226">Als u bijvoorbeeld de register sleutel HKLM\Software in het HKLM: station van een ander station wilt weer geven, typt u:</span><span class="sxs-lookup"><span data-stu-id="accfb-226">For example, to view the HKLM\Software registry key in the HKLM: drive from another drive, type:</span></span>

```powershell
Get-ChildItem HKLM:\SOFTWARE\
```

<span data-ttu-id="accfb-227">Als u het station wilt openen, gebruikt u de cmdlet Set-Location.</span><span class="sxs-lookup"><span data-stu-id="accfb-227">To open the drive, use the Set-Location cmdlet.</span></span> <span data-ttu-id="accfb-228">Onthoud de dubbele punt wanneer u het stationspad opgeeft.</span><span class="sxs-lookup"><span data-stu-id="accfb-228">Remember the colon when you specify the drive path.</span></span> <span data-ttu-id="accfb-229">Als u bijvoorbeeld de locatie wilt wijzigen in de hoofdmap van het certificaat: station, typt u:</span><span class="sxs-lookup"><span data-stu-id="accfb-229">For example, to change your location to the root directory of the Cert: drive, type:</span></span>

```powershell
Set-Location cert:
```

<span data-ttu-id="accfb-230">Om de inhoud van het certificaat te bekijken: station, typt u:</span><span class="sxs-lookup"><span data-stu-id="accfb-230">Then, to view the contents of the Cert: drive, type:</span></span>

```powershell
Get-ChildItem
```

## <a name="moving-through-hierarchical-data"></a><span data-ttu-id="accfb-231">Overstappen op hiërarchische gegevens</span><span class="sxs-lookup"><span data-stu-id="accfb-231">Moving through hierarchical data</span></span>

<span data-ttu-id="accfb-232">U kunt een provider station verplaatsen op dezelfde manier als een harde schijf.</span><span class="sxs-lookup"><span data-stu-id="accfb-232">You can move through a provider drive just as you would a hard disk drive.</span></span>
<span data-ttu-id="accfb-233">Als de gegevens in een hiërarchie van items binnen items zijn gerangschikt, gebruikt u een back slash ( `\` ) om een onderliggend item aan te duiden.</span><span class="sxs-lookup"><span data-stu-id="accfb-233">If the data is arranged in a hierarchy of items within items, use a backslash (`\`) to indicate a child item.</span></span> <span data-ttu-id="accfb-234">Gebruik de volgende indeling:</span><span class="sxs-lookup"><span data-stu-id="accfb-234">Use the following format:</span></span>

```
drive:\location\child-location\...
```

<span data-ttu-id="accfb-235">Als u bijvoorbeeld uw locatie wilt wijzigen in de register sleutel HKLM\Software, typt u een Set-Location opdracht, bijvoorbeeld:</span><span class="sxs-lookup"><span data-stu-id="accfb-235">For example, to change your location to the HKLM\Software registry key, type a Set-Location command, such as:</span></span>

```powershell
Set-Location HKLM:\SOFTWARE\
```

<span data-ttu-id="accfb-236">Als een element in de volledig gekwalificeerde naam spaties bevat, moet u de naam tussen dubbele aanhalings tekens ( `"` ) plaatsen.</span><span class="sxs-lookup"><span data-stu-id="accfb-236">If any element in the fully qualified name includes spaces, you must enclose the name in double-quotation marks (`"`).</span></span> <span data-ttu-id="accfb-237">In het volgende voor beeld ziet u een volledig gekwalificeerd pad dat spaties bevat.</span><span class="sxs-lookup"><span data-stu-id="accfb-237">The following example shows a fully qualified path that includes spaces.</span></span>

```
"C:\Program Files\Internet Explorer\iexplore.exe"
```

<span data-ttu-id="accfb-238">U kunt ook relatieve verwijzingen naar locaties gebruiken.</span><span class="sxs-lookup"><span data-stu-id="accfb-238">You can also use relative references to locations.</span></span> <span data-ttu-id="accfb-239">Een punt ( `.` ) staat voor de huidige locatie.</span><span class="sxs-lookup"><span data-stu-id="accfb-239">A dot (`.`) represents the current location.</span></span> <span data-ttu-id="accfb-240">Als u bijvoorbeeld in de `HKLM:\Software\Microsoft` register sleutel bent en u de registersubsleutels in de sleutel wilt weer geven `HKLM:\Software\Microsoft\PowerShell` , typt u de volgende opdracht:</span><span class="sxs-lookup"><span data-stu-id="accfb-240">For example, if you are in the `HKLM:\Software\Microsoft` registry key, and you want to list the registry subkeys in the `HKLM:\Software\Microsoft\PowerShell` key, type the following command:</span></span>

```powershell
Get-ChildItem .\PowerShell
```

<span data-ttu-id="accfb-241">Dubbele punten ( `..` ) verwijst ook naar de map of container direct boven uw huidige locatie.</span><span class="sxs-lookup"><span data-stu-id="accfb-241">Also, double-dots (`..`) refers to the directory or container directly above your current location.</span></span> <span data-ttu-id="accfb-242">U kunt dubbele punten () gebruiken `..` om te navigeren door een provider hiërarchie.</span><span class="sxs-lookup"><span data-stu-id="accfb-242">You can use double-dots (`..`) to navigate through a provider hierarchy.</span></span>

```
PS HKLM:\SYSTEM\CurrentControlSet\Services\LanmanServer\Parameters\> cd ..\..\LanmanWorkstation\Parameters
PS HKLM:\SYSTEM\CurrentControlSet\Services\LanmanWorkstation\Parameters>
```

## <a name="provider-home"></a><span data-ttu-id="accfb-243">Start pagina van provider</span><span class="sxs-lookup"><span data-stu-id="accfb-243">Provider Home</span></span>

<span data-ttu-id="accfb-244">Providers hebben ook een **thuis** locatie.</span><span class="sxs-lookup"><span data-stu-id="accfb-244">Providers also have a **Home** location.</span></span>  <span data-ttu-id="accfb-245">Deze locatie wordt gedeeld door `PSDrives` de provider.</span><span class="sxs-lookup"><span data-stu-id="accfb-245">This location is shared by all `PSDrives` backed by the provider.</span></span> <span data-ttu-id="accfb-246">Het kan worden opgehaald door de **Start** -eigenschap van de provider weer te geven.</span><span class="sxs-lookup"><span data-stu-id="accfb-246">It can be retrieved by viewing the **Home** property of the provider.</span></span>

```powershell
Get-PSProvider | Format-Table Name, Home
```

```Output
Name        Home
----        ----
Registry
Alias
Environment
FileSystem  C:\Users\username
Function
Variable
Certificate
```

<span data-ttu-id="accfb-247">De **File System** provider is de enige provider met een standaard waarde voor **Home**.</span><span class="sxs-lookup"><span data-stu-id="accfb-247">The **FileSystem** provider is the only provider that has a default value for **Home**.</span></span> <span data-ttu-id="accfb-248">Dit is dezelfde waarde als `$Home` .</span><span class="sxs-lookup"><span data-stu-id="accfb-248">It's the same value as `$Home`.</span></span> <span data-ttu-id="accfb-249">Zie [about_Automatic_Variables](about_Automatic_Variables.md)voor meer informatie.</span><span class="sxs-lookup"><span data-stu-id="accfb-249">For more information, see [about_Automatic_Variables](about_Automatic_Variables.md).</span></span>

<span data-ttu-id="accfb-250">U kunt de **basis** Directory voor een provider voor de huidige sessie instellen met behulp van de eigenschap.</span><span class="sxs-lookup"><span data-stu-id="accfb-250">You can set the **Home** directory for a provider, for the current session, using its property.</span></span>

```powershell
(Get-PSProvider FileSystem).Home = "C:\"
```

<span data-ttu-id="accfb-251">Het `~` teken kan worden gebruikt om de basismap van de provider weer te geven.</span><span class="sxs-lookup"><span data-stu-id="accfb-251">The `~` character can be used to represent the provider's home directory.</span></span>
<span data-ttu-id="accfb-252">Als er geen **thuis** locatie is ingesteld voor de provider, ziet u een fout melding.</span><span class="sxs-lookup"><span data-stu-id="accfb-252">If the provider doesn't have a **Home** location set, you see an error.</span></span>

```powershell
Cert:\> Set-Location ~
```

```Output
Set-Location : Home location for this provider isn't set. To set the home
location, call "(get-psprovider 'Certificate').Home = 'path'".
At line:1 char:1
+ Set-Location ~
+ ~~~~~~~~~~~~~~
    + CategoryInfo          : InvalidOperation: (:) [Set-Location],
                              PSInvalidOperationException
...
```

## <a name="finding-dynamic-parameters"></a><span data-ttu-id="accfb-253">Dynamische para meters zoeken</span><span class="sxs-lookup"><span data-stu-id="accfb-253">Finding dynamic parameters</span></span>

<span data-ttu-id="accfb-254">Dynamische para meters zijn cmdlet-para meters die worden toegevoegd aan een cmdlet door een provider.</span><span class="sxs-lookup"><span data-stu-id="accfb-254">Dynamic parameters are cmdlet parameters that are added to a cmdlet by a provider.</span></span> <span data-ttu-id="accfb-255">Deze para meters zijn alleen beschikbaar wanneer de cmdlet wordt gebruikt met de provider die deze heeft toegevoegd.</span><span class="sxs-lookup"><span data-stu-id="accfb-255">These parameters are available only when the cmdlet is used with the provider that added them.</span></span>

<span data-ttu-id="accfb-256">Het `Cert:` station voegt bijvoorbeeld de para meter **CodeSigningCert** toe aan de `Get-Item` `Get-ChildItem` cmdlets en.</span><span class="sxs-lookup"><span data-stu-id="accfb-256">For example, the `Cert:` drive adds the **CodeSigningCert** parameter to the `Get-Item` and `Get-ChildItem` cmdlets.</span></span> <span data-ttu-id="accfb-257">U kunt deze para meter alleen gebruiken wanneer u `Get-Item` of `Get-ChildItem` in het `Cert:` station gebruikt.</span><span class="sxs-lookup"><span data-stu-id="accfb-257">You can use this parameter only when you use `Get-Item` or `Get-ChildItem` in the `Cert:` drive.</span></span>

<span data-ttu-id="accfb-258">Zie het Help-bestand voor de provider voor een lijst met de dynamische para meters die een provider ondersteunt.</span><span class="sxs-lookup"><span data-stu-id="accfb-258">For a list of the dynamic parameters that a provider supports, see the Help file for the provider.</span></span> <span data-ttu-id="accfb-259">Type:</span><span class="sxs-lookup"><span data-stu-id="accfb-259">Type:</span></span>

```
Get-Help <provider-name>
```

<span data-ttu-id="accfb-260">Bijvoorbeeld:</span><span class="sxs-lookup"><span data-stu-id="accfb-260">For example:</span></span>

```powershell
Get-Help certificate
```

## <a name="learning-about-providers"></a><span data-ttu-id="accfb-261">Informatie over providers</span><span class="sxs-lookup"><span data-stu-id="accfb-261">Learning about providers</span></span>

<span data-ttu-id="accfb-262">Hoewel alle provider gegevens worden weer gegeven in stations en u dezelfde methoden gebruikt om ze te door lopen, wordt de overeenkomst daar gestopt.</span><span class="sxs-lookup"><span data-stu-id="accfb-262">Although all provider data appears in drives and you use the same methods to move through them, the similarity stops there.</span></span> <span data-ttu-id="accfb-263">De gegevens archieven die de provider beschikbaar maakt, kunnen variëren als Active Directory locaties en post vakken van micro soft Exchange Server.</span><span class="sxs-lookup"><span data-stu-id="accfb-263">The data stores that the provider exposes can be as varied as Active Directory locations and Microsoft Exchange Server mailboxes.</span></span>

<span data-ttu-id="accfb-264">Voor informatie over afzonderlijke Power shell-providers typt u:</span><span class="sxs-lookup"><span data-stu-id="accfb-264">For information about individual PowerShell providers, type:</span></span>

```
Get-Help <ProviderName>
```

<span data-ttu-id="accfb-265">Bijvoorbeeld:</span><span class="sxs-lookup"><span data-stu-id="accfb-265">For example:</span></span>

```powershell
Get-Help registry
```

<span data-ttu-id="accfb-266">Voor een lijst met Help-onderwerpen over de providers, typt u:</span><span class="sxs-lookup"><span data-stu-id="accfb-266">For a list of Help topics about the providers, type:</span></span>

```powershell
Get-Help * -Category Provider
```

## <a name="see-also"></a><span data-ttu-id="accfb-267">Zie ook</span><span class="sxs-lookup"><span data-stu-id="accfb-267">See also</span></span>

[<span data-ttu-id="accfb-268">about_Locations</span><span class="sxs-lookup"><span data-stu-id="accfb-268">about_Locations</span></span>](about_Locations.md)

[<span data-ttu-id="accfb-269">about_Path_Syntax</span><span class="sxs-lookup"><span data-stu-id="accfb-269">about_Path_Syntax</span></span>](about_Path_Syntax.md)
