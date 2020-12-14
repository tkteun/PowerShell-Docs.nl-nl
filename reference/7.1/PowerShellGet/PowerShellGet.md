---
Download Help Link: https://aka.ms/powershell71-help
Help Version: 7.1.0.0
keywords: powershell,cmdlet
Locale: en-US
Module Guid: 1d73a601-4a6c-43c5-ba3f-619b18bbb404
Module Name: PowerShellGet
ms.date: 06/09/2017
schema: 2.0.0
title: PowerShellGet
ms.openlocfilehash: 577dc9a56da98d975b777e6cd48ecdcaafd3128d
ms.sourcegitcommit: 22c93550c87af30c4895fcb9e9dd65e30d60ada0
ms.translationtype: MT
ms.contentlocale: nl-NL
ms.lasthandoff: 11/19/2020
ms.locfileid: "94892366"
---
# <span data-ttu-id="8bf0b-103">PowerShellGet-module</span><span class="sxs-lookup"><span data-stu-id="8bf0b-103">PowerShellGet Module</span></span>

## <span data-ttu-id="8bf0b-104">Description</span><span class="sxs-lookup"><span data-stu-id="8bf0b-104">Description</span></span>

<span data-ttu-id="8bf0b-105">PowerShellGet is een module met opdrachten voor het detecteren, installeren, bijwerken en publiceren van Power shell-artefacten, zoals modules, DSC-resources, functie mogelijkheden en scripts.</span><span class="sxs-lookup"><span data-stu-id="8bf0b-105">PowerShellGet is a module with commands for discovering, installing, updating and publishing PowerShell artifacts like Modules, DSC Resources, Role Capabilities, and Scripts.</span></span>

> [!IMPORTANT]
> <span data-ttu-id="8bf0b-106">Vanaf april 2020 biedt de PowerShell Gallery niet langer ondersteuning voor Transport Layer Security (TLS) versie 1,0 en 1,1.</span><span class="sxs-lookup"><span data-stu-id="8bf0b-106">As of April 2020, the PowerShell Gallery no longer supports Transport Layer Security (TLS) versions 1.0 and 1.1.</span></span> <span data-ttu-id="8bf0b-107">Als u geen TLS 1,2 of hoger gebruikt, wordt er een fout bericht weer gegeven wanneer u probeert toegang te krijgen tot de PowerShell Gallery.</span><span class="sxs-lookup"><span data-stu-id="8bf0b-107">If you are not using TLS 1.2 or higher, you will receive an error when trying to access the PowerShell Gallery.</span></span> <span data-ttu-id="8bf0b-108">Gebruik de volgende opdracht om ervoor te zorgen dat u TLS 1,2 gebruikt:</span><span class="sxs-lookup"><span data-stu-id="8bf0b-108">Use the following command to ensure you are using TLS 1.2:</span></span>
>
> `[Net.ServicePointManager]::SecurityProtocol = [Net.SecurityProtocolType]::Tls12`
>
> <span data-ttu-id="8bf0b-109">Zie de [aankondiging](https://devblogs.microsoft.com/powershell/powershell-gallery-tls-support/) in het Power shell-blog voor meer informatie.</span><span class="sxs-lookup"><span data-stu-id="8bf0b-109">For more information, see the [announcement](https://devblogs.microsoft.com/powershell/powershell-gallery-tls-support/) in the PowerShell blog.</span></span>

## <span data-ttu-id="8bf0b-110">PowerShellGet-cmdlets</span><span class="sxs-lookup"><span data-stu-id="8bf0b-110">PowerShellGet Cmdlets</span></span>

### [<span data-ttu-id="8bf0b-111">Zoeken-opdracht</span><span class="sxs-lookup"><span data-stu-id="8bf0b-111">Find-Command</span></span>](Find-Command.md)
<span data-ttu-id="8bf0b-112">Hiermee vindt u Power shell-opdrachten in modules.</span><span class="sxs-lookup"><span data-stu-id="8bf0b-112">Finds PowerShell commands in modules.</span></span>

### [<span data-ttu-id="8bf0b-113">Zoeken-Dscresource bieden</span><span class="sxs-lookup"><span data-stu-id="8bf0b-113">Find-DscResource</span></span>](Find-DscResource.md)
<span data-ttu-id="8bf0b-114">Zoekt naar desired state Configuration (DSC)-resources.</span><span class="sxs-lookup"><span data-stu-id="8bf0b-114">Finds Desired State Configuration (DSC) resources.</span></span>

### [<span data-ttu-id="8bf0b-115">Find-Module</span><span class="sxs-lookup"><span data-stu-id="8bf0b-115">Find-Module</span></span>](Find-Module.md)
<span data-ttu-id="8bf0b-116">Hiermee worden modules in een opslag plaats gevonden die overeenkomen met opgegeven criteria.</span><span class="sxs-lookup"><span data-stu-id="8bf0b-116">Finds modules in a repository that match specified criteria.</span></span>

### [<span data-ttu-id="8bf0b-117">Zoeken-RoleCapability</span><span class="sxs-lookup"><span data-stu-id="8bf0b-117">Find-RoleCapability</span></span>](Find-RoleCapability.md)
<span data-ttu-id="8bf0b-118">Hiermee vindt u functie mogelijkheden in modules.</span><span class="sxs-lookup"><span data-stu-id="8bf0b-118">Finds role capabilities in modules.</span></span>

### [<span data-ttu-id="8bf0b-119">Zoeken-script</span><span class="sxs-lookup"><span data-stu-id="8bf0b-119">Find-Script</span></span>](Find-Script.md)
<span data-ttu-id="8bf0b-120">Zoekt naar een script.</span><span class="sxs-lookup"><span data-stu-id="8bf0b-120">Finds a script.</span></span>

### [<span data-ttu-id="8bf0b-121">Get-InstalledModule</span><span class="sxs-lookup"><span data-stu-id="8bf0b-121">Get-InstalledModule</span></span>](Get-InstalledModule.md)
<span data-ttu-id="8bf0b-122">Hiermee wordt een lijst met modules opgehaald op de computer die is geïnstalleerd door PowerShellGet.</span><span class="sxs-lookup"><span data-stu-id="8bf0b-122">Gets a list of modules on the computer that were installed by PowerShellGet.</span></span>

### [<span data-ttu-id="8bf0b-123">Get-InstalledScript</span><span class="sxs-lookup"><span data-stu-id="8bf0b-123">Get-InstalledScript</span></span>](Get-InstalledScript.md)
<span data-ttu-id="8bf0b-124">Hiermee wordt een geïnstalleerd script opgehaald.</span><span class="sxs-lookup"><span data-stu-id="8bf0b-124">Gets an installed script.</span></span>

### [<span data-ttu-id="8bf0b-125">Get-PSRepository</span><span class="sxs-lookup"><span data-stu-id="8bf0b-125">Get-PSRepository</span></span>](Get-PSRepository.md)
<span data-ttu-id="8bf0b-126">Hiermee worden Power shell-opslag plaatsen opgehaald.</span><span class="sxs-lookup"><span data-stu-id="8bf0b-126">Gets PowerShell repositories.</span></span>

### [<span data-ttu-id="8bf0b-127">Installatie-module</span><span class="sxs-lookup"><span data-stu-id="8bf0b-127">Install-Module</span></span>](Install-Module.md)
<span data-ttu-id="8bf0b-128">Hiermee downloadt u een of meer modules uit een opslag plaats en installeert u deze op de lokale computer.</span><span class="sxs-lookup"><span data-stu-id="8bf0b-128">Downloads one or more modules from a repository, and installs them on the local computer.</span></span>

### [<span data-ttu-id="8bf0b-129">Install-script</span><span class="sxs-lookup"><span data-stu-id="8bf0b-129">Install-Script</span></span>](Install-Script.md)
<span data-ttu-id="8bf0b-130">Hiermee wordt een script geïnstalleerd.</span><span class="sxs-lookup"><span data-stu-id="8bf0b-130">Installs a script.</span></span>

### [<span data-ttu-id="8bf0b-131">New-ScriptFileInfo</span><span class="sxs-lookup"><span data-stu-id="8bf0b-131">New-ScriptFileInfo</span></span>](New-ScriptFileInfo.md)
<span data-ttu-id="8bf0b-132">Hiermee maakt u een script bestand met meta gegevens.</span><span class="sxs-lookup"><span data-stu-id="8bf0b-132">Creates a script file with metadata.</span></span>

### [<span data-ttu-id="8bf0b-133">Publish-Module</span><span class="sxs-lookup"><span data-stu-id="8bf0b-133">Publish-Module</span></span>](Publish-Module.md)
<span data-ttu-id="8bf0b-134">Hiermee publiceert u een opgegeven module van de lokale computer naar een online galerie.</span><span class="sxs-lookup"><span data-stu-id="8bf0b-134">Publishes a specified module from the local computer to an online gallery.</span></span>

### [<span data-ttu-id="8bf0b-135">Publish-Script</span><span class="sxs-lookup"><span data-stu-id="8bf0b-135">Publish-Script</span></span>](Publish-Script.md)
<span data-ttu-id="8bf0b-136">Publiceert een script.</span><span class="sxs-lookup"><span data-stu-id="8bf0b-136">Publishes a script.</span></span>

### [<span data-ttu-id="8bf0b-137">REGI ster-PSRepository</span><span class="sxs-lookup"><span data-stu-id="8bf0b-137">Register-PSRepository</span></span>](Register-PSRepository.md)
<span data-ttu-id="8bf0b-138">Registreert een Power shell-opslag plaats.</span><span class="sxs-lookup"><span data-stu-id="8bf0b-138">Registers a PowerShell repository.</span></span>

### [<span data-ttu-id="8bf0b-139">Save-Module</span><span class="sxs-lookup"><span data-stu-id="8bf0b-139">Save-Module</span></span>](Save-Module.md)
<span data-ttu-id="8bf0b-140">Slaat een module en de bijbehorende afhankelijkheden op de lokale computer op, maar installeert de module niet.</span><span class="sxs-lookup"><span data-stu-id="8bf0b-140">Saves a module and its dependencies on the local computer but doesn't install the module.</span></span>

### [<span data-ttu-id="8bf0b-141">Save-Script</span><span class="sxs-lookup"><span data-stu-id="8bf0b-141">Save-Script</span></span>](Save-Script.md)
<span data-ttu-id="8bf0b-142">Slaat een script op.</span><span class="sxs-lookup"><span data-stu-id="8bf0b-142">Saves a script.</span></span>

### [<span data-ttu-id="8bf0b-143">Set-PSRepository</span><span class="sxs-lookup"><span data-stu-id="8bf0b-143">Set-PSRepository</span></span>](Set-PSRepository.md)
<span data-ttu-id="8bf0b-144">Hiermee stelt u waarden in voor een geregistreerde opslag plaats.</span><span class="sxs-lookup"><span data-stu-id="8bf0b-144">Sets values for a registered repository.</span></span>

### [<span data-ttu-id="8bf0b-145">Test-ScriptFileInfo</span><span class="sxs-lookup"><span data-stu-id="8bf0b-145">Test-ScriptFileInfo</span></span>](Test-ScriptFileInfo.md)
<span data-ttu-id="8bf0b-146">Hiermee wordt een opmerkingen blok voor een script gevalideerd.</span><span class="sxs-lookup"><span data-stu-id="8bf0b-146">Validates a comment block for a script.</span></span>

### [<span data-ttu-id="8bf0b-147">Uninstall-module</span><span class="sxs-lookup"><span data-stu-id="8bf0b-147">Uninstall-Module</span></span>](Uninstall-Module.md)
<span data-ttu-id="8bf0b-148">Hiermee verwijdert u een module.</span><span class="sxs-lookup"><span data-stu-id="8bf0b-148">Uninstalls a module.</span></span>

### [<span data-ttu-id="8bf0b-149">Uninstall-script</span><span class="sxs-lookup"><span data-stu-id="8bf0b-149">Uninstall-Script</span></span>](Uninstall-Script.md)
<span data-ttu-id="8bf0b-150">Hiermee verwijdert u een script.</span><span class="sxs-lookup"><span data-stu-id="8bf0b-150">Uninstalls a script.</span></span>

### [<span data-ttu-id="8bf0b-151">Registratie ongedaan maken-PSRepository</span><span class="sxs-lookup"><span data-stu-id="8bf0b-151">Unregister-PSRepository</span></span>](Unregister-PSRepository.md)
<span data-ttu-id="8bf0b-152">Hiermee wordt de registratie van een opslag plaats ongedaan gemaakt.</span><span class="sxs-lookup"><span data-stu-id="8bf0b-152">Unregisters a repository.</span></span>

### [<span data-ttu-id="8bf0b-153">Update-Module</span><span class="sxs-lookup"><span data-stu-id="8bf0b-153">Update-Module</span></span>](Update-Module.md)
<span data-ttu-id="8bf0b-154">Downloadt en installeert de nieuwste versie van de opgegeven modules van een online galerie naar de lokale computer.</span><span class="sxs-lookup"><span data-stu-id="8bf0b-154">Downloads and installs the newest version of specified modules from an online gallery to the local computer.</span></span>

### [<span data-ttu-id="8bf0b-155">Update-ModuleManifest</span><span class="sxs-lookup"><span data-stu-id="8bf0b-155">Update-ModuleManifest</span></span>](Update-ModuleManifest.md)
<span data-ttu-id="8bf0b-156">Hiermee wordt een manifest bestand van de module bijgewerkt.</span><span class="sxs-lookup"><span data-stu-id="8bf0b-156">Updates a module manifest file.</span></span>

### [<span data-ttu-id="8bf0b-157">Update-script</span><span class="sxs-lookup"><span data-stu-id="8bf0b-157">Update-Script</span></span>](Update-Script.md)
<span data-ttu-id="8bf0b-158">Hiermee wordt een script bijgewerkt.</span><span class="sxs-lookup"><span data-stu-id="8bf0b-158">Updates a script.</span></span>

### [<span data-ttu-id="8bf0b-159">Update-ScriptFileInfo</span><span class="sxs-lookup"><span data-stu-id="8bf0b-159">Update-ScriptFileInfo</span></span>](Update-ScriptFileInfo.md)
<span data-ttu-id="8bf0b-160">Hiermee wordt informatie over een script bijgewerkt.</span><span class="sxs-lookup"><span data-stu-id="8bf0b-160">Updates information for a script.</span></span>
