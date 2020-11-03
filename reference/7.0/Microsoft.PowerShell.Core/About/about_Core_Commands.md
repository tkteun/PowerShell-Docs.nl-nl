---
description: Een lijst met de cmdlets die zijn ontworpen voor gebruik met Power shell-providers.
keywords: powershell,cmdlet
Locale: en-US
ms.date: 06/09/2017
online version: https://docs.microsoft.com/powershell/module/microsoft.powershell.core/about/about_core_commands?view=powershell-7&WT.mc_id=ps-gethelp
schema: 2.0.0
title: about_Core_Commands
ms.openlocfilehash: 5c784518ae30108813d32497f654198e7d10b379
ms.sourcegitcommit: f874dc1d4236e06a3df195d179f59e0a7d9f8436
ms.translationtype: MT
ms.contentlocale: nl-NL
ms.lasthandoff: 10/13/2020
ms.locfileid: "93252112"
---
# <a name="about-core-commands"></a><span data-ttu-id="27001-104">Over kern opdrachten</span><span class="sxs-lookup"><span data-stu-id="27001-104">About Core Commands</span></span>

## <a name="short-description"></a><span data-ttu-id="27001-105">KORTE BESCHRIJVING</span><span class="sxs-lookup"><span data-stu-id="27001-105">SHORT DESCRIPTION</span></span>
<span data-ttu-id="27001-106">Een lijst met de cmdlets die zijn ontworpen voor gebruik met Power shell-providers.</span><span class="sxs-lookup"><span data-stu-id="27001-106">Lists the cmdlets that are designed for use with PowerShell providers.</span></span>

## <a name="long-description"></a><span data-ttu-id="27001-107">LANGE BESCHRIJVING</span><span class="sxs-lookup"><span data-stu-id="27001-107">LONG DESCRIPTION</span></span>

<span data-ttu-id="27001-108">Power shell bevat een set cmdlets die specifiek zijn ontworpen voor het beheren van de items in de gegevens archieven die door Power shell-providers worden weer gegeven.</span><span class="sxs-lookup"><span data-stu-id="27001-108">PowerShell includes a set of cmdlets that are specifically designed to manage the items in the data stores that are exposed by PowerShell providers.</span></span>
<span data-ttu-id="27001-109">U kunt deze cmdlets op dezelfde manier gebruiken om alle verschillende soorten gegevens te beheren die de providers voor u beschikbaar maken.</span><span class="sxs-lookup"><span data-stu-id="27001-109">You can use these cmdlets in the same ways to manage all the different types of data that the providers make available to you.</span></span> <span data-ttu-id="27001-110">Typ "Get-Help about_providers" voor meer informatie over providers.</span><span class="sxs-lookup"><span data-stu-id="27001-110">For more information about providers, type "get-help about_providers".</span></span>

<span data-ttu-id="27001-111">U kunt bijvoorbeeld de cmdlet Get-ChildItem gebruiken om de bestanden in een map van het bestands systeem, de sleutels onder een register sleutel of de items die worden weer gegeven door een provider die u schrijft of downloadt, weer te geven.</span><span class="sxs-lookup"><span data-stu-id="27001-111">For example, you can use the Get-ChildItem cmdlet to list the files in a file system directory, the keys under a registry key, or the items that are exposed by a provider that you write or download.</span></span>

<span data-ttu-id="27001-112">Hier volgt een lijst met de Power shell-cmdlets die zijn ontworpen voor gebruik met providers:</span><span class="sxs-lookup"><span data-stu-id="27001-112">The following is a list of the PowerShell cmdlets that are designed for use with providers:</span></span>

<span data-ttu-id="27001-113">Child item-cmdlets</span><span class="sxs-lookup"><span data-stu-id="27001-113">ChildItem cmdlets</span></span>

- <span data-ttu-id="27001-114">Get-ChildItem</span><span class="sxs-lookup"><span data-stu-id="27001-114">Get-ChildItem</span></span>

<span data-ttu-id="27001-115">Cmdlets voor inhoud</span><span class="sxs-lookup"><span data-stu-id="27001-115">Content cmdlets</span></span>

- <span data-ttu-id="27001-116">Add-Content</span><span class="sxs-lookup"><span data-stu-id="27001-116">Add-Content</span></span>
- <span data-ttu-id="27001-117">Clear-Content</span><span class="sxs-lookup"><span data-stu-id="27001-117">Clear-Content</span></span>
- <span data-ttu-id="27001-118">Get-Content</span><span class="sxs-lookup"><span data-stu-id="27001-118">Get-Content</span></span>
- <span data-ttu-id="27001-119">Set-Content</span><span class="sxs-lookup"><span data-stu-id="27001-119">Set-Content</span></span>

<span data-ttu-id="27001-120">Cmdlets voor items</span><span class="sxs-lookup"><span data-stu-id="27001-120">Item cmdlets</span></span>

- <span data-ttu-id="27001-121">Clear-Item</span><span class="sxs-lookup"><span data-stu-id="27001-121">Clear-Item</span></span>
- <span data-ttu-id="27001-122">Copy-Item</span><span class="sxs-lookup"><span data-stu-id="27001-122">Copy-Item</span></span>
- <span data-ttu-id="27001-123">Get-Item</span><span class="sxs-lookup"><span data-stu-id="27001-123">Get-Item</span></span>
- <span data-ttu-id="27001-124">Invoke-Item</span><span class="sxs-lookup"><span data-stu-id="27001-124">Invoke-Item</span></span>
- <span data-ttu-id="27001-125">Move-Item</span><span class="sxs-lookup"><span data-stu-id="27001-125">Move-Item</span></span>
- <span data-ttu-id="27001-126">New-Item</span><span class="sxs-lookup"><span data-stu-id="27001-126">New-Item</span></span>
- <span data-ttu-id="27001-127">Remove-Item</span><span class="sxs-lookup"><span data-stu-id="27001-127">Remove-Item</span></span>
- <span data-ttu-id="27001-128">Rename-Item</span><span class="sxs-lookup"><span data-stu-id="27001-128">Rename-Item</span></span>
- <span data-ttu-id="27001-129">Set-Item</span><span class="sxs-lookup"><span data-stu-id="27001-129">Set-Item</span></span>

<span data-ttu-id="27001-130">Item Property-cmdlets</span><span class="sxs-lookup"><span data-stu-id="27001-130">ItemProperty cmdlets</span></span>

- <span data-ttu-id="27001-131">Clear-ItemProperty</span><span class="sxs-lookup"><span data-stu-id="27001-131">Clear-ItemProperty</span></span>
- <span data-ttu-id="27001-132">Copy-ItemProperty</span><span class="sxs-lookup"><span data-stu-id="27001-132">Copy-ItemProperty</span></span>
- <span data-ttu-id="27001-133">Get-ItemProperty</span><span class="sxs-lookup"><span data-stu-id="27001-133">Get-ItemProperty</span></span>
- <span data-ttu-id="27001-134">Move-ItemProperty</span><span class="sxs-lookup"><span data-stu-id="27001-134">Move-ItemProperty</span></span>
- <span data-ttu-id="27001-135">New-ItemProperty</span><span class="sxs-lookup"><span data-stu-id="27001-135">New-ItemProperty</span></span>
- <span data-ttu-id="27001-136">Remove-ItemProperty</span><span class="sxs-lookup"><span data-stu-id="27001-136">Remove-ItemProperty</span></span>
- <span data-ttu-id="27001-137">Rename-ItemProperty</span><span class="sxs-lookup"><span data-stu-id="27001-137">Rename-ItemProperty</span></span>
- <span data-ttu-id="27001-138">Set-ItemProperty</span><span class="sxs-lookup"><span data-stu-id="27001-138">Set-ItemProperty</span></span>

<span data-ttu-id="27001-139">Locatie-cmdlets</span><span class="sxs-lookup"><span data-stu-id="27001-139">Location cmdlets</span></span>

- <span data-ttu-id="27001-140">Get-Location</span><span class="sxs-lookup"><span data-stu-id="27001-140">Get-Location</span></span>
- <span data-ttu-id="27001-141">Pop-Location</span><span class="sxs-lookup"><span data-stu-id="27001-141">Pop-Location</span></span>
- <span data-ttu-id="27001-142">Push-Location</span><span class="sxs-lookup"><span data-stu-id="27001-142">Push-Location</span></span>
- <span data-ttu-id="27001-143">Set-Location</span><span class="sxs-lookup"><span data-stu-id="27001-143">Set-Location</span></span>

<span data-ttu-id="27001-144">Pad-cmdlets</span><span class="sxs-lookup"><span data-stu-id="27001-144">Path cmdlets</span></span>

- <span data-ttu-id="27001-145">Join-Path</span><span class="sxs-lookup"><span data-stu-id="27001-145">Join-Path</span></span>
- <span data-ttu-id="27001-146">Convert-Path</span><span class="sxs-lookup"><span data-stu-id="27001-146">Convert-Path</span></span>
- <span data-ttu-id="27001-147">Split-Path</span><span class="sxs-lookup"><span data-stu-id="27001-147">Split-Path</span></span>
- <span data-ttu-id="27001-148">Resolve-Path</span><span class="sxs-lookup"><span data-stu-id="27001-148">Resolve-Path</span></span>
- <span data-ttu-id="27001-149">Test-Path</span><span class="sxs-lookup"><span data-stu-id="27001-149">Test-Path</span></span>

<span data-ttu-id="27001-150">PSDrive-cmdlets</span><span class="sxs-lookup"><span data-stu-id="27001-150">PSDrive cmdlets</span></span>

- <span data-ttu-id="27001-151">Get-PSDrive</span><span class="sxs-lookup"><span data-stu-id="27001-151">Get-PSDrive</span></span>
- <span data-ttu-id="27001-152">New-PSDrive</span><span class="sxs-lookup"><span data-stu-id="27001-152">New-PSDrive</span></span>
- <span data-ttu-id="27001-153">Remove-PSDrive</span><span class="sxs-lookup"><span data-stu-id="27001-153">Remove-PSDrive</span></span>

<span data-ttu-id="27001-154">PSProvider-cmdlets</span><span class="sxs-lookup"><span data-stu-id="27001-154">PSProvider cmdlets</span></span>

- <span data-ttu-id="27001-155">Get-PSProvider</span><span class="sxs-lookup"><span data-stu-id="27001-155">Get-PSProvider</span></span>

<span data-ttu-id="27001-156">Typ voor meer informatie over een cmdlet `get-help <cmdlet-name>` .</span><span class="sxs-lookup"><span data-stu-id="27001-156">For more information about a cmdlet, type `get-help <cmdlet-name>`.</span></span>

## <a name="see-also"></a><span data-ttu-id="27001-157">ZIE OOK</span><span class="sxs-lookup"><span data-stu-id="27001-157">SEE ALSO</span></span>

[<span data-ttu-id="27001-158">about_Providers</span><span class="sxs-lookup"><span data-stu-id="27001-158">about_Providers</span></span>](about_Providers.md)
