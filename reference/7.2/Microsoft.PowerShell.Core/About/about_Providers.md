---
description: Hierin wordt beschreven hoe Power shell-providers toegang bieden tot gegevens en onderdelen die anders niet eenvoudig toegankelijk zijn via de opdracht regel. De gegevens worden weer gegeven in een consistente indeling die lijkt op een bestandssysteem station.
Locale: en-US
ms.date: 03/27/2020
online version: https://docs.microsoft.com/powershell/module/microsoft.powershell.core/about/about_providers?view=powershell-7.2&WT.mc_id=ps-gethelp
schema: 2.0.0
title: about_Providers
ms.openlocfilehash: 6073ef13a6d0a02cded69073d7ffaef903a807ea
ms.sourcegitcommit: 95d41698c7a2450eeb70ef2fb6507fe7e6eff3b6
ms.translationtype: MT
ms.contentlocale: nl-NL
ms.lasthandoff: 11/17/2020
ms.locfileid: "94705517"
---
# <a name="about-providers"></a><span data-ttu-id="b3950-104">Over providers</span><span class="sxs-lookup"><span data-stu-id="b3950-104">About Providers</span></span>

## <a name="short-description"></a><span data-ttu-id="b3950-105">Korte beschrijving</span><span class="sxs-lookup"><span data-stu-id="b3950-105">Short description</span></span>
<span data-ttu-id="b3950-106">Hierin wordt beschreven hoe Power shell-providers toegang bieden tot gegevens en onderdelen die anders niet eenvoudig toegankelijk zijn via de opdracht regel.</span><span class="sxs-lookup"><span data-stu-id="b3950-106">Describes how PowerShell providers provide access to data and components that wouldn't otherwise be easily accessible at the command line.</span></span>
<span data-ttu-id="b3950-107">De gegevens worden weer gegeven in een consistente indeling die lijkt op een bestandssysteem station.</span><span class="sxs-lookup"><span data-stu-id="b3950-107">The data is presented in a consistent format that resembles a file system drive.</span></span>

## <a name="long-description"></a><span data-ttu-id="b3950-108">Lange beschrijving</span><span class="sxs-lookup"><span data-stu-id="b3950-108">Long description</span></span>

<span data-ttu-id="b3950-109">Power shell-providers zijn .NET-Program ma's die toegang bieden tot gespecialiseerde gegevens archieven, zodat ze eenvoudiger kunnen worden bekeken en beheerd.</span><span class="sxs-lookup"><span data-stu-id="b3950-109">PowerShell providers are .NET programs that provide access to specialized data stores for easier viewing and management.</span></span> <span data-ttu-id="b3950-110">De gegevens worden weer gegeven in een station en u hebt toegang tot de gegevens in een pad zoals u zou doen op een harde schijf.</span><span class="sxs-lookup"><span data-stu-id="b3950-110">The data appears in a drive, and you access the data in a path like you would on a hard disk drive.</span></span> <span data-ttu-id="b3950-111">U kunt een van de ingebouwde cmdlets gebruiken die door de provider worden ondersteund voor het beheren van de gegevens in het provider station.</span><span class="sxs-lookup"><span data-stu-id="b3950-111">You can use any of the built-in cmdlets that the provider supports to manage the data in the provider drive.</span></span> <span data-ttu-id="b3950-112">En u kunt aangepaste cmdlets gebruiken die speciaal zijn ontworpen voor de gegevens.</span><span class="sxs-lookup"><span data-stu-id="b3950-112">And, you can use custom cmdlets that are designed especially for the data.</span></span>

<span data-ttu-id="b3950-113">De providers kunnen ook dynamische para meters toevoegen aan de ingebouwde cmdlets.</span><span class="sxs-lookup"><span data-stu-id="b3950-113">The providers can also add dynamic parameters to the built-in cmdlets.</span></span> <span data-ttu-id="b3950-114">Deze para meters zijn alleen beschikbaar wanneer u de cmdlet met de provider gegevens gebruikt.</span><span class="sxs-lookup"><span data-stu-id="b3950-114">These parameters are only available when you use the cmdlet with the provider data.</span></span>

## <a name="built-in-providers"></a><span data-ttu-id="b3950-115">Ingebouwde providers</span><span class="sxs-lookup"><span data-stu-id="b3950-115">Built-in providers</span></span>

<span data-ttu-id="b3950-116">Power shell bevat een set ingebouwde providers die u kunt gebruiken om toegang te krijgen tot de verschillende typen gegevens archieven.</span><span class="sxs-lookup"><span data-stu-id="b3950-116">PowerShell includes a set of built-in providers that you can use to access the different types of data stores.</span></span>

| <span data-ttu-id="b3950-117">Provider</span><span class="sxs-lookup"><span data-stu-id="b3950-117">Provider</span></span>   |   <span data-ttu-id="b3950-118">Station (s)</span><span class="sxs-lookup"><span data-stu-id="b3950-118">Drive(s)</span></span>  |<span data-ttu-id="b3950-119">Type</span><span class="sxs-lookup"><span data-stu-id="b3950-119">OutputType</span></span>                                                    |
|----------- |------------ |--------------------------------------------------------------|
|<span data-ttu-id="b3950-120">Alias</span><span class="sxs-lookup"><span data-stu-id="b3950-120">Alias</span></span>       |<span data-ttu-id="b3950-121">Toe</span><span class="sxs-lookup"><span data-stu-id="b3950-121">Alias:</span></span>       |<span data-ttu-id="b3950-122">System. Management. Automation. AliasInfo</span><span class="sxs-lookup"><span data-stu-id="b3950-122">System.Management.Automation.AliasInfo</span></span>                        |
|<span data-ttu-id="b3950-123">Certificaat</span><span class="sxs-lookup"><span data-stu-id="b3950-123">Certificate</span></span> |<span data-ttu-id="b3950-124">Certificaat</span><span class="sxs-lookup"><span data-stu-id="b3950-124">Cert:</span></span>        |<span data-ttu-id="b3950-125">Micro soft. Power shell. commands. X509StoreLocation</span><span class="sxs-lookup"><span data-stu-id="b3950-125">Microsoft.PowerShell.Commands.X509StoreLocation</span></span>               |
|            |             |<span data-ttu-id="b3950-126">System. Security. Cryptography. X509Certificates. X509Certificate2</span><span class="sxs-lookup"><span data-stu-id="b3950-126">System.Security.Cryptography.X509Certificates.X509Certificate2</span></span>|
|<span data-ttu-id="b3950-127">Omgeving</span><span class="sxs-lookup"><span data-stu-id="b3950-127">Environment</span></span> |<span data-ttu-id="b3950-128">Envelop</span><span class="sxs-lookup"><span data-stu-id="b3950-128">Env:</span></span>         |<span data-ttu-id="b3950-129">System. Collections. Dictionary entry</span><span class="sxs-lookup"><span data-stu-id="b3950-129">System.Collections.DictionaryEntry</span></span>                            |
|<span data-ttu-id="b3950-130">Bestandssysteem</span><span class="sxs-lookup"><span data-stu-id="b3950-130">FileSystem</span></span>  |<span data-ttu-id="b3950-131">C: (\*)</span><span class="sxs-lookup"><span data-stu-id="b3950-131">C: (\*)</span></span>       |<span data-ttu-id="b3950-132">System. IO. file info</span><span class="sxs-lookup"><span data-stu-id="b3950-132">System.IO.FileInfo</span></span>                                            |
|            |             |<span data-ttu-id="b3950-133">System. IO. DirectoryInfo</span><span class="sxs-lookup"><span data-stu-id="b3950-133">System.IO.DirectoryInfo</span></span>                                       |
|<span data-ttu-id="b3950-134">Functie</span><span class="sxs-lookup"><span data-stu-id="b3950-134">Function</span></span>    |<span data-ttu-id="b3950-135">Functieassembly</span><span class="sxs-lookup"><span data-stu-id="b3950-135">Function:</span></span>    |<span data-ttu-id="b3950-136">System. Management. Automation. FunctionInfo</span><span class="sxs-lookup"><span data-stu-id="b3950-136">System.Management.Automation.FunctionInfo</span></span>                     |
|<span data-ttu-id="b3950-137">Register</span><span class="sxs-lookup"><span data-stu-id="b3950-137">Registry</span></span>    |<span data-ttu-id="b3950-138">HKLM: HKCU:</span><span class="sxs-lookup"><span data-stu-id="b3950-138">HKLM: HKCU:</span></span>  |<span data-ttu-id="b3950-139">Microsoft. Win32. RegistryKey</span><span class="sxs-lookup"><span data-stu-id="b3950-139">Microsoft.Win32.RegistryKey</span></span>                                   |
|<span data-ttu-id="b3950-140">Variabele</span><span class="sxs-lookup"><span data-stu-id="b3950-140">Variable</span></span>    |<span data-ttu-id="b3950-141">Variabeletype</span><span class="sxs-lookup"><span data-stu-id="b3950-141">Variable:</span></span>    |<span data-ttu-id="b3950-142">System. Management. Automation. PSVariable</span><span class="sxs-lookup"><span data-stu-id="b3950-142">System.Management.Automation.PSVariable</span></span>                       |
|<span data-ttu-id="b3950-143">WSMan</span><span class="sxs-lookup"><span data-stu-id="b3950-143">WSMan</span></span>       |<span data-ttu-id="b3950-144">WSMan</span><span class="sxs-lookup"><span data-stu-id="b3950-144">WSMan:</span></span>       |<span data-ttu-id="b3950-145">Micro soft. WSMan. Management. WSManConfigContainerElement</span><span class="sxs-lookup"><span data-stu-id="b3950-145">Microsoft.WSMan.Management.WSManConfigContainerElement</span></span>        |

<span data-ttu-id="b3950-146">(\*) De stations van het bestands systeem variëren per systeem.</span><span class="sxs-lookup"><span data-stu-id="b3950-146">(\*) The FileSystem drives vary on each system.</span></span>

<span data-ttu-id="b3950-147">U kunt ook uw eigen Power shell-providers maken en u kunt providers installeren die anderen ontwikkelen.</span><span class="sxs-lookup"><span data-stu-id="b3950-147">You can also create your own PowerShell providers, and you can install providers that others develop.</span></span> <span data-ttu-id="b3950-148">Als u een lijst wilt weer geven van de providers die beschikbaar zijn in uw sessie, typt u:</span><span class="sxs-lookup"><span data-stu-id="b3950-148">To list the providers that are available in your session, type:</span></span>

```powershell
Get-PSProvider
```

## <a name="installing-and-removing-providers"></a><span data-ttu-id="b3950-149">Providers installeren en verwijderen</span><span class="sxs-lookup"><span data-stu-id="b3950-149">Installing and removing providers</span></span>

<span data-ttu-id="b3950-150">Providers worden doorgaans geïnstalleerd via Power shell-modules.</span><span class="sxs-lookup"><span data-stu-id="b3950-150">Providers are typically installed via PowerShell modules.</span></span> <span data-ttu-id="b3950-151">Als u de module importeert, wordt de provider in uw sessie geladen.</span><span class="sxs-lookup"><span data-stu-id="b3950-151">Importing the module loads the provider into your session.</span></span> <span data-ttu-id="b3950-152">U kunt de ingebouwde providers niet verwijderen.</span><span class="sxs-lookup"><span data-stu-id="b3950-152">You can't uninstall the built-in providers.</span></span> <span data-ttu-id="b3950-153">U kunt de door andere modules geladen providers verwijderen.</span><span class="sxs-lookup"><span data-stu-id="b3950-153">You can uninstall providers loaded by other modules.</span></span>

<span data-ttu-id="b3950-154">U kunt een provider uit de huidige sessie verwijderen met de `Remove-Module` cmdlet.</span><span class="sxs-lookup"><span data-stu-id="b3950-154">You can unload a provider from the current session using the `Remove-Module` cmdlet.</span></span> <span data-ttu-id="b3950-155">Met deze cmdlet wordt de provider niet verwijderd, maar wordt de provider niet beschikbaar in de sessie.</span><span class="sxs-lookup"><span data-stu-id="b3950-155">This cmdlet doesn't uninstall the provider, but it makes the provider unavailable in the session.</span></span>

<span data-ttu-id="b3950-156">U kunt ook de `Remove-PSDrive` cmdlet gebruiken om een station uit de huidige sessie te verwijderen.</span><span class="sxs-lookup"><span data-stu-id="b3950-156">You can also use the `Remove-PSDrive` cmdlet to remove any drive from the current session.</span></span> <span data-ttu-id="b3950-157">Deze gegevens op het station worden niet beïnvloed, maar het station is niet meer beschikbaar in die sessie.</span><span class="sxs-lookup"><span data-stu-id="b3950-157">This data on the drive isn't affected, but the drive is no longer available in that session.</span></span>

## <a name="viewing-providers"></a><span data-ttu-id="b3950-158">Providers weer geven</span><span class="sxs-lookup"><span data-stu-id="b3950-158">Viewing providers</span></span>

<span data-ttu-id="b3950-159">Als u de Power shell-providers op uw computer wilt weer geven, typt u:</span><span class="sxs-lookup"><span data-stu-id="b3950-159">To view the PowerShell providers on your computer, type:</span></span>

```powershell
Get-PSProvider
```

<span data-ttu-id="b3950-160">De uitvoer bevat een lijst met de ingebouwde providers en de providers die u hebt toegevoegd aan de sessie.</span><span class="sxs-lookup"><span data-stu-id="b3950-160">The output lists the built-in providers and the providers that you added to the session.</span></span>

## <a name="the-provider-cmdlets"></a><span data-ttu-id="b3950-161">De provider-cmdlets</span><span class="sxs-lookup"><span data-stu-id="b3950-161">The provider cmdlets</span></span>

<span data-ttu-id="b3950-162">De volgende cmdlets zijn ontworpen om te werken met de gegevens die door elke provider worden weer gegeven.</span><span class="sxs-lookup"><span data-stu-id="b3950-162">The following cmdlets are designed to work with the data exposed by any provider.</span></span> <span data-ttu-id="b3950-163">U kunt dezelfde cmdlets op dezelfde manier gebruiken voor het beheren van de verschillende typen gegevens die providers beschikbaar maken.</span><span class="sxs-lookup"><span data-stu-id="b3950-163">You can use the same cmdlets in the same way to manage the different types of data that providers expose.</span></span> <span data-ttu-id="b3950-164">Wanneer u de gegevens van een provider hebt beheerd, kunt u dezelfde procedures gebruiken met de gegevens van een provider.</span><span class="sxs-lookup"><span data-stu-id="b3950-164">After you learn to manage the data of one provider, you can use the same procedures with the data from any provider.</span></span>

<span data-ttu-id="b3950-165">Met de `New-Item` cmdlet maakt u bijvoorbeeld een nieuw item.</span><span class="sxs-lookup"><span data-stu-id="b3950-165">For example, the `New-Item` cmdlet creates a new item.</span></span> <span data-ttu-id="b3950-166">In het `C:` station dat door de **File System** provider wordt ondersteund, kunt u gebruiken `New-Item` om een nieuw bestand of nieuwe map te maken.</span><span class="sxs-lookup"><span data-stu-id="b3950-166">In the `C:` drive that is supported by the **FileSystem** provider, you can use `New-Item` to create a new file or folder.</span></span> <span data-ttu-id="b3950-167">In de stations die worden ondersteund door de **register** provider, kunt u gebruiken `New-Item` om een nieuwe register sleutel te maken.</span><span class="sxs-lookup"><span data-stu-id="b3950-167">In the drives that are supported by the **Registry** provider, you can use `New-Item` to create a new registry key.</span></span> <span data-ttu-id="b3950-168">In het `Alias:` station kunt u gebruiken `New-Item` om een nieuwe alias te maken.</span><span class="sxs-lookup"><span data-stu-id="b3950-168">In the `Alias:` drive, you can use `New-Item` to create a new alias.</span></span>

<span data-ttu-id="b3950-169">Voor gedetailleerde informatie over een van de volgende cmdlets, typt u:</span><span class="sxs-lookup"><span data-stu-id="b3950-169">For detailed information about any of the following cmdlets, type:</span></span>

```
Get-Help <cmdlet-name> -Detailed
```

### <a name="childitem-cmdlets"></a><span data-ttu-id="b3950-170">Child item-cmdlets</span><span class="sxs-lookup"><span data-stu-id="b3950-170">ChildItem cmdlets</span></span>

- [<span data-ttu-id="b3950-171">Get-Child item</span><span class="sxs-lookup"><span data-stu-id="b3950-171">Get-ChildItem</span></span>](xref:Microsoft.PowerShell.Management.Get-ChildItem)

### <a name="content-cmdlets"></a><span data-ttu-id="b3950-172">Cmdlets voor inhoud</span><span class="sxs-lookup"><span data-stu-id="b3950-172">Content Cmdlets</span></span>

- [<span data-ttu-id="b3950-173">Add-content</span><span class="sxs-lookup"><span data-stu-id="b3950-173">Add-Content</span></span>](xref:Microsoft.PowerShell.Management.Add-Content)
- [<span data-ttu-id="b3950-174">Wissen-inhoud</span><span class="sxs-lookup"><span data-stu-id="b3950-174">Clear-Content</span></span>](xref:Microsoft.PowerShell.Management.Clear-Content)
- [<span data-ttu-id="b3950-175">Get-Content</span><span class="sxs-lookup"><span data-stu-id="b3950-175">Get-Content</span></span>](xref:Microsoft.PowerShell.Management.Get-Content)
- [<span data-ttu-id="b3950-176">Set-Content</span><span class="sxs-lookup"><span data-stu-id="b3950-176">Set-Content</span></span>](xref:Microsoft.PowerShell.Management.Set-Content)

### <a name="item-cmdlets"></a><span data-ttu-id="b3950-177">Cmdlets voor items</span><span class="sxs-lookup"><span data-stu-id="b3950-177">Item Cmdlets</span></span>

- [<span data-ttu-id="b3950-178">Wissen-item</span><span class="sxs-lookup"><span data-stu-id="b3950-178">Clear-Item</span></span>](xref:Microsoft.PowerShell.Management.Clear-Item)
- [<span data-ttu-id="b3950-179">Kopie-item</span><span class="sxs-lookup"><span data-stu-id="b3950-179">Copy-Item</span></span>](xref:Microsoft.PowerShell.Management.Copy-Item)
- [<span data-ttu-id="b3950-180">Get-item</span><span class="sxs-lookup"><span data-stu-id="b3950-180">Get-Item</span></span>](xref:Microsoft.PowerShell.Management.Get-Item)
- [<span data-ttu-id="b3950-181">Invoke-item</span><span class="sxs-lookup"><span data-stu-id="b3950-181">Invoke-Item</span></span>](xref:Microsoft.PowerShell.Management.Invoke-Item)
- [<span data-ttu-id="b3950-182">Item verplaatsen</span><span class="sxs-lookup"><span data-stu-id="b3950-182">Move-Item</span></span>](xref:Microsoft.PowerShell.Management.Move-Item)
- [<span data-ttu-id="b3950-183">Nieuw-item</span><span class="sxs-lookup"><span data-stu-id="b3950-183">New-Item</span></span>](xref:Microsoft.PowerShell.Management.New-Item)
- [<span data-ttu-id="b3950-184">Verwijderen-item</span><span class="sxs-lookup"><span data-stu-id="b3950-184">Remove-Item</span></span>](xref:Microsoft.PowerShell.Management.Remove-Item)
- [<span data-ttu-id="b3950-185">Naam wijzigen-item</span><span class="sxs-lookup"><span data-stu-id="b3950-185">Rename-Item</span></span>](xref:Microsoft.PowerShell.Management.Rename-Item)
- [<span data-ttu-id="b3950-186">Set-item</span><span class="sxs-lookup"><span data-stu-id="b3950-186">Set-Item</span></span>](xref:Microsoft.PowerShell.Management.Set-Item)

### <a name="itemproperty-cmdlets"></a><span data-ttu-id="b3950-187">Item Property-cmdlets</span><span class="sxs-lookup"><span data-stu-id="b3950-187">ItemProperty cmdlets</span></span>

- [<span data-ttu-id="b3950-188">Wissen-item Property</span><span class="sxs-lookup"><span data-stu-id="b3950-188">Clear-ItemProperty</span></span>](xref:Microsoft.PowerShell.Management.Clear-ItemProperty)
- [<span data-ttu-id="b3950-189">Kopiëren-item Property</span><span class="sxs-lookup"><span data-stu-id="b3950-189">Copy-ItemProperty</span></span>](xref:Microsoft.PowerShell.Management.Copy-ItemProperty)
- [<span data-ttu-id="b3950-190">Get-item Property</span><span class="sxs-lookup"><span data-stu-id="b3950-190">Get-ItemProperty</span></span>](xref:Microsoft.PowerShell.Management.Get-ItemProperty)
- [<span data-ttu-id="b3950-191">Verplaatsen-item Property</span><span class="sxs-lookup"><span data-stu-id="b3950-191">Move-ItemProperty</span></span>](xref:Microsoft.PowerShell.Management.Move-ItemProperty)
- [<span data-ttu-id="b3950-192">Nieuw-item Property</span><span class="sxs-lookup"><span data-stu-id="b3950-192">New-ItemProperty</span></span>](xref:Microsoft.PowerShell.Management.New-ItemProperty)
- [<span data-ttu-id="b3950-193">Verwijderen-item Property</span><span class="sxs-lookup"><span data-stu-id="b3950-193">Remove-ItemProperty</span></span>](xref:Microsoft.PowerShell.Management.Remove-ItemProperty)
- [<span data-ttu-id="b3950-194">Naam wijzigen-item Property</span><span class="sxs-lookup"><span data-stu-id="b3950-194">Rename-ItemProperty</span></span>](xref:Microsoft.PowerShell.Management.Rename-ItemProperty)
- [<span data-ttu-id="b3950-195">Set-item Property</span><span class="sxs-lookup"><span data-stu-id="b3950-195">Set-ItemProperty</span></span>](xref:Microsoft.PowerShell.Management.Set-ItemProperty)

### <a name="location-cmdlets"></a><span data-ttu-id="b3950-196">Locatie-cmdlets</span><span class="sxs-lookup"><span data-stu-id="b3950-196">Location cmdlets</span></span>

- [<span data-ttu-id="b3950-197">Get-locatie</span><span class="sxs-lookup"><span data-stu-id="b3950-197">Get-Location</span></span>](xref:Microsoft.PowerShell.Management.Get-Location)
- [<span data-ttu-id="b3950-198">Pop-locatie</span><span class="sxs-lookup"><span data-stu-id="b3950-198">Pop-Location</span></span>](xref:Microsoft.PowerShell.Management.Pop-Location)
- [<span data-ttu-id="b3950-199">Push-locatie</span><span class="sxs-lookup"><span data-stu-id="b3950-199">Push-Location</span></span>](xref:Microsoft.PowerShell.Management.Push-Location)
- [<span data-ttu-id="b3950-200">Set-Location</span><span class="sxs-lookup"><span data-stu-id="b3950-200">Set-Location</span></span>](xref:Microsoft.PowerShell.Management.Set-Location)

### <a name="path-cmdlets"></a><span data-ttu-id="b3950-201">Pad-cmdlets</span><span class="sxs-lookup"><span data-stu-id="b3950-201">Path cmdlets</span></span>

- [<span data-ttu-id="b3950-202">Pad voor samen voegen</span><span class="sxs-lookup"><span data-stu-id="b3950-202">Join-Path</span></span>](xref:Microsoft.PowerShell.Management.Join-Path)
- [<span data-ttu-id="b3950-203">Convert-pad</span><span class="sxs-lookup"><span data-stu-id="b3950-203">Convert-Path</span></span>](xref:Microsoft.PowerShell.Management.Convert-Path)
- [<span data-ttu-id="b3950-204">Split-pad</span><span class="sxs-lookup"><span data-stu-id="b3950-204">Split-Path</span></span>](xref:Microsoft.PowerShell.Management.Split-Path)
- [<span data-ttu-id="b3950-205">Oplossen-pad</span><span class="sxs-lookup"><span data-stu-id="b3950-205">Resolve-Path</span></span>](xref:Microsoft.PowerShell.Management.Resolve-Path)
- [<span data-ttu-id="b3950-206">Test-pad</span><span class="sxs-lookup"><span data-stu-id="b3950-206">Test-Path</span></span>](xref:Microsoft.PowerShell.Management.Test-Path)

### <a name="psdrive-cmdlets"></a><span data-ttu-id="b3950-207">PSDrive-cmdlets</span><span class="sxs-lookup"><span data-stu-id="b3950-207">PSDrive cmdlets</span></span>

- [<span data-ttu-id="b3950-208">Get-PSDrive</span><span class="sxs-lookup"><span data-stu-id="b3950-208">Get-PSDrive</span></span>](xref:Microsoft.PowerShell.Management.Get-PSDrive)
- [<span data-ttu-id="b3950-209">New-PSDrive</span><span class="sxs-lookup"><span data-stu-id="b3950-209">New-PSDrive</span></span>](xref:Microsoft.PowerShell.Management.New-PSDrive)
- [<span data-ttu-id="b3950-210">Remove-PSDrive</span><span class="sxs-lookup"><span data-stu-id="b3950-210">Remove-PSDrive</span></span>](xref:Microsoft.PowerShell.Management.Remove-PSDrive)

### <a name="psprovider-cmdlets"></a><span data-ttu-id="b3950-211">PSProvider-cmdlets</span><span class="sxs-lookup"><span data-stu-id="b3950-211">PSProvider Cmdlets</span></span>

- [<span data-ttu-id="b3950-212">Get-PSProvider</span><span class="sxs-lookup"><span data-stu-id="b3950-212">Get-PSProvider</span></span>](xref:Microsoft.PowerShell.Management.Get-PSProvider)

## <a name="viewing-provider-data"></a><span data-ttu-id="b3950-213">Provider gegevens weer geven</span><span class="sxs-lookup"><span data-stu-id="b3950-213">Viewing provider data</span></span>

<span data-ttu-id="b3950-214">Het belangrijkste voor deel van een provider is dat de gegevens op een vertrouwde en consistente manier beschikbaar worden gesteld.</span><span class="sxs-lookup"><span data-stu-id="b3950-214">The primary benefit of a provider is that it exposes its data in a familiar and consistent way.</span></span> <span data-ttu-id="b3950-215">Het model voor gegevens presentatie is een bestandssysteem station.</span><span class="sxs-lookup"><span data-stu-id="b3950-215">The model for data presentation is a file system drive.</span></span>

<span data-ttu-id="b3950-216">Met de provider kunt u items in het gegevens archief weer geven, navigeren en wijzigen, alsof deze gegevens in een bestands systeem waren.</span><span class="sxs-lookup"><span data-stu-id="b3950-216">The provider allows you to view, navigate, and change items in the data store as though they were data in a file system.</span></span> <span data-ttu-id="b3950-217">Het gegevens archief wordt geopend met de naam van het station dat wordt ondersteund.</span><span class="sxs-lookup"><span data-stu-id="b3950-217">The data store is accessed by the name of the drive that it supports.</span></span>

<span data-ttu-id="b3950-218">Het station wordt weer gegeven in de standaard weergave van de `Get-PSProvider` cmdlet, maar u kunt informatie over het provider station verkrijgen met de `Get-PSDrive` cmdlet.</span><span class="sxs-lookup"><span data-stu-id="b3950-218">The drive is listed in the default display of the `Get-PSProvider` cmdlet, but you can get information about the provider drive using the `Get-PSDrive` cmdlet.</span></span> <span data-ttu-id="b3950-219">Als u bijvoorbeeld alle eigenschappen van de functie wilt ophalen: station, typt u:</span><span class="sxs-lookup"><span data-stu-id="b3950-219">For example, to get all the properties of the Function: drive, type:</span></span>

```powershell
Get-PSDrive Function | Format-List *
```

<span data-ttu-id="b3950-220">U kunt de gegevens in een provider station bekijken en verplaatsen op dezelfde manier als op een bestandssysteem station.</span><span class="sxs-lookup"><span data-stu-id="b3950-220">You can view and move through the data in a provider drive just as you would on a file system drive.</span></span>

<span data-ttu-id="b3950-221">Als u de inhoud van een provider station wilt weer geven, gebruikt u de Get-Item-of Get-ChildItem-cmdlets.</span><span class="sxs-lookup"><span data-stu-id="b3950-221">To view the contents of a provider drive, use the Get-Item or Get-ChildItem cmdlets.</span></span> <span data-ttu-id="b3950-222">Typ de naam van het station gevolgd door een dubbele punt (:).</span><span class="sxs-lookup"><span data-stu-id="b3950-222">Type the drive name followed by a colon (:).</span></span> <span data-ttu-id="b3950-223">Als u bijvoorbeeld de inhoud van de alias wilt bekijken: station, typt u:</span><span class="sxs-lookup"><span data-stu-id="b3950-223">For example, to view the contents of the Alias: drive, type:</span></span>

```powershell
Get-Item alias:
```

<span data-ttu-id="b3950-224">U kunt de gegevens in een wille keurig station weer geven en beheren vanaf een ander station door de naam van het station in het pad op te nemen.</span><span class="sxs-lookup"><span data-stu-id="b3950-224">You can view and manage the data in any drive from another drive by including the drive name in the path.</span></span> <span data-ttu-id="b3950-225">Als u bijvoorbeeld de register sleutel HKLM\Software in het HKLM: station van een ander station wilt weer geven, typt u:</span><span class="sxs-lookup"><span data-stu-id="b3950-225">For example, to view the HKLM\Software registry key in the HKLM: drive from another drive, type:</span></span>

```powershell
Get-ChildItem HKLM:\SOFTWARE\
```

<span data-ttu-id="b3950-226">Als u het station wilt openen, gebruikt u de cmdlet Set-Location.</span><span class="sxs-lookup"><span data-stu-id="b3950-226">To open the drive, use the Set-Location cmdlet.</span></span> <span data-ttu-id="b3950-227">Onthoud de dubbele punt wanneer u het stationspad opgeeft.</span><span class="sxs-lookup"><span data-stu-id="b3950-227">Remember the colon when you specify the drive path.</span></span> <span data-ttu-id="b3950-228">Als u bijvoorbeeld de locatie wilt wijzigen in de hoofdmap van het certificaat: station, typt u:</span><span class="sxs-lookup"><span data-stu-id="b3950-228">For example, to change your location to the root directory of the Cert: drive, type:</span></span>

```powershell
Set-Location cert:
```

<span data-ttu-id="b3950-229">Om de inhoud van het certificaat te bekijken: station, typt u:</span><span class="sxs-lookup"><span data-stu-id="b3950-229">Then, to view the contents of the Cert: drive, type:</span></span>

```powershell
Get-ChildItem
```

## <a name="moving-through-hierarchical-data"></a><span data-ttu-id="b3950-230">Overstappen op hiërarchische gegevens</span><span class="sxs-lookup"><span data-stu-id="b3950-230">Moving through hierarchical data</span></span>

<span data-ttu-id="b3950-231">U kunt een provider station verplaatsen op dezelfde manier als een harde schijf.</span><span class="sxs-lookup"><span data-stu-id="b3950-231">You can move through a provider drive just as you would a hard disk drive.</span></span>
<span data-ttu-id="b3950-232">Als de gegevens in een hiërarchie van items binnen items zijn gerangschikt, gebruikt u een back slash ( `\` ) om een onderliggend item aan te duiden.</span><span class="sxs-lookup"><span data-stu-id="b3950-232">If the data is arranged in a hierarchy of items within items, use a backslash (`\`) to indicate a child item.</span></span> <span data-ttu-id="b3950-233">Gebruik de volgende indeling:</span><span class="sxs-lookup"><span data-stu-id="b3950-233">Use the following format:</span></span>

```
drive:\location\child-location\...
```

<span data-ttu-id="b3950-234">Als u bijvoorbeeld uw locatie wilt wijzigen in de register sleutel HKLM\Software, typt u een Set-Location opdracht, bijvoorbeeld:</span><span class="sxs-lookup"><span data-stu-id="b3950-234">For example, to change your location to the HKLM\Software registry key, type a Set-Location command, such as:</span></span>

```powershell
Set-Location HKLM:\SOFTWARE\
```

<span data-ttu-id="b3950-235">Als een element in de volledig gekwalificeerde naam spaties bevat, moet u de naam tussen dubbele aanhalings tekens ( `"` ) plaatsen.</span><span class="sxs-lookup"><span data-stu-id="b3950-235">If any element in the fully qualified name includes spaces, you must enclose the name in double-quotation marks (`"`).</span></span> <span data-ttu-id="b3950-236">In het volgende voor beeld ziet u een volledig gekwalificeerd pad dat spaties bevat.</span><span class="sxs-lookup"><span data-stu-id="b3950-236">The following example shows a fully qualified path that includes spaces.</span></span>

```
"C:\Program Files\Internet Explorer\iexplore.exe"
```

<span data-ttu-id="b3950-237">U kunt ook relatieve verwijzingen naar locaties gebruiken.</span><span class="sxs-lookup"><span data-stu-id="b3950-237">You can also use relative references to locations.</span></span> <span data-ttu-id="b3950-238">Een punt ( `.` ) staat voor de huidige locatie.</span><span class="sxs-lookup"><span data-stu-id="b3950-238">A dot (`.`) represents the current location.</span></span> <span data-ttu-id="b3950-239">Als u bijvoorbeeld in de `HKLM:\Software\Microsoft` register sleutel bent en u de registersubsleutels in de sleutel wilt weer geven `HKLM:\Software\Microsoft\PowerShell` , typt u de volgende opdracht:</span><span class="sxs-lookup"><span data-stu-id="b3950-239">For example, if you are in the `HKLM:\Software\Microsoft` registry key, and you want to list the registry subkeys in the `HKLM:\Software\Microsoft\PowerShell` key, type the following command:</span></span>

```powershell
Get-ChildItem .\PowerShell
```

<span data-ttu-id="b3950-240">Dubbele punten ( `..` ) verwijst ook naar de map of container direct boven uw huidige locatie.</span><span class="sxs-lookup"><span data-stu-id="b3950-240">Also, double-dots (`..`) refers to the directory or container directly above your current location.</span></span> <span data-ttu-id="b3950-241">U kunt dubbele punten () gebruiken `..` om te navigeren door een provider hiërarchie.</span><span class="sxs-lookup"><span data-stu-id="b3950-241">You can use double-dots (`..`) to navigate through a provider hierarchy.</span></span>

```
PS HKLM:\SYSTEM\CurrentControlSet\Services\LanmanServer\Parameters\> cd ..\..\LanmanWorkstation\Parameters
PS HKLM:\SYSTEM\CurrentControlSet\Services\LanmanWorkstation\Parameters>
```

## <a name="provider-home"></a><span data-ttu-id="b3950-242">Start pagina van provider</span><span class="sxs-lookup"><span data-stu-id="b3950-242">Provider Home</span></span>

<span data-ttu-id="b3950-243">Providers hebben ook een **thuis** locatie.</span><span class="sxs-lookup"><span data-stu-id="b3950-243">Providers also have a **Home** location.</span></span>  <span data-ttu-id="b3950-244">Deze locatie wordt gedeeld door `PSDrives` de provider.</span><span class="sxs-lookup"><span data-stu-id="b3950-244">This location is shared by all `PSDrives` backed by the provider.</span></span> <span data-ttu-id="b3950-245">Het kan worden opgehaald door de **Start** -eigenschap van de provider weer te geven.</span><span class="sxs-lookup"><span data-stu-id="b3950-245">It can be retrieved by viewing the **Home** property of the provider.</span></span>

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

<span data-ttu-id="b3950-246">De **File System** provider is de enige provider met een standaard waarde voor **Home**.</span><span class="sxs-lookup"><span data-stu-id="b3950-246">The **FileSystem** provider is the only provider that has a default value for **Home**.</span></span> <span data-ttu-id="b3950-247">Dit is dezelfde waarde als `$Home` .</span><span class="sxs-lookup"><span data-stu-id="b3950-247">It's the same value as `$Home`.</span></span> <span data-ttu-id="b3950-248">Zie [about_Automatic_Variables](about_Automatic_Variables.md)voor meer informatie.</span><span class="sxs-lookup"><span data-stu-id="b3950-248">For more information, see [about_Automatic_Variables](about_Automatic_Variables.md).</span></span>

<span data-ttu-id="b3950-249">U kunt de **basis** Directory voor een provider voor de huidige sessie instellen met behulp van de eigenschap.</span><span class="sxs-lookup"><span data-stu-id="b3950-249">You can set the **Home** directory for a provider, for the current session, using its property.</span></span>

```powershell
(Get-PSProvider FileSystem).Home = "C:\"
```

<span data-ttu-id="b3950-250">Het `~` teken kan worden gebruikt om de basismap van de provider weer te geven.</span><span class="sxs-lookup"><span data-stu-id="b3950-250">The `~` character can be used to represent the provider's home directory.</span></span>
<span data-ttu-id="b3950-251">Als er geen **thuis** locatie is ingesteld voor de provider, ziet u een fout melding.</span><span class="sxs-lookup"><span data-stu-id="b3950-251">If the provider doesn't have a **Home** location set, you see an error.</span></span>

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

## <a name="finding-dynamic-parameters"></a><span data-ttu-id="b3950-252">Dynamische para meters zoeken</span><span class="sxs-lookup"><span data-stu-id="b3950-252">Finding dynamic parameters</span></span>

<span data-ttu-id="b3950-253">Dynamische para meters zijn cmdlet-para meters die worden toegevoegd aan een cmdlet door een provider.</span><span class="sxs-lookup"><span data-stu-id="b3950-253">Dynamic parameters are cmdlet parameters that are added to a cmdlet by a provider.</span></span> <span data-ttu-id="b3950-254">Deze para meters zijn alleen beschikbaar wanneer de cmdlet wordt gebruikt met de provider die deze heeft toegevoegd.</span><span class="sxs-lookup"><span data-stu-id="b3950-254">These parameters are available only when the cmdlet is used with the provider that added them.</span></span>

<span data-ttu-id="b3950-255">Het `Cert:` station voegt bijvoorbeeld de para meter **CodeSigningCert** toe aan de `Get-Item` `Get-ChildItem` cmdlets en.</span><span class="sxs-lookup"><span data-stu-id="b3950-255">For example, the `Cert:` drive adds the **CodeSigningCert** parameter to the `Get-Item` and `Get-ChildItem` cmdlets.</span></span> <span data-ttu-id="b3950-256">U kunt deze para meter alleen gebruiken wanneer u `Get-Item` of `Get-ChildItem` in het `Cert:` station gebruikt.</span><span class="sxs-lookup"><span data-stu-id="b3950-256">You can use this parameter only when you use `Get-Item` or `Get-ChildItem` in the `Cert:` drive.</span></span>

<span data-ttu-id="b3950-257">Zie het Help-bestand voor de provider voor een lijst met de dynamische para meters die een provider ondersteunt.</span><span class="sxs-lookup"><span data-stu-id="b3950-257">For a list of the dynamic parameters that a provider supports, see the Help file for the provider.</span></span> <span data-ttu-id="b3950-258">Type:</span><span class="sxs-lookup"><span data-stu-id="b3950-258">Type:</span></span>

```
Get-Help <provider-name>
```

<span data-ttu-id="b3950-259">Bijvoorbeeld:</span><span class="sxs-lookup"><span data-stu-id="b3950-259">For example:</span></span>

```powershell
Get-Help certificate
```

## <a name="learning-about-providers"></a><span data-ttu-id="b3950-260">Informatie over providers</span><span class="sxs-lookup"><span data-stu-id="b3950-260">Learning about providers</span></span>

<span data-ttu-id="b3950-261">Hoewel alle provider gegevens worden weer gegeven in stations en u dezelfde methoden gebruikt om ze te door lopen, wordt de overeenkomst daar gestopt.</span><span class="sxs-lookup"><span data-stu-id="b3950-261">Although all provider data appears in drives and you use the same methods to move through them, the similarity stops there.</span></span> <span data-ttu-id="b3950-262">De gegevens archieven die de provider beschikbaar maakt, kunnen variëren als Active Directory locaties en post vakken van micro soft Exchange Server.</span><span class="sxs-lookup"><span data-stu-id="b3950-262">The data stores that the provider exposes can be as varied as Active Directory locations and Microsoft Exchange Server mailboxes.</span></span>

<span data-ttu-id="b3950-263">Voor informatie over afzonderlijke Power shell-providers typt u:</span><span class="sxs-lookup"><span data-stu-id="b3950-263">For information about individual PowerShell providers, type:</span></span>

```
Get-Help <ProviderName>
```

<span data-ttu-id="b3950-264">Bijvoorbeeld:</span><span class="sxs-lookup"><span data-stu-id="b3950-264">For example:</span></span>

```powershell
Get-Help registry
```

<span data-ttu-id="b3950-265">Voor een lijst met Help-onderwerpen over de providers, typt u:</span><span class="sxs-lookup"><span data-stu-id="b3950-265">For a list of Help topics about the providers, type:</span></span>

```powershell
Get-Help * -Category Provider
```

## <a name="see-also"></a><span data-ttu-id="b3950-266">Zie ook</span><span class="sxs-lookup"><span data-stu-id="b3950-266">See also</span></span>

[<span data-ttu-id="b3950-267">about_Locations</span><span class="sxs-lookup"><span data-stu-id="b3950-267">about_Locations</span></span>](about_Locations.md)

[<span data-ttu-id="b3950-268">about_Path_Syntax</span><span class="sxs-lookup"><span data-stu-id="b3950-268">about_Path_Syntax</span></span>](about_Path_Syntax.md)

