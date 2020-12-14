---
Download Help Link: https://aka.ms/powershell71-help
Help Version: 7.1.0.0
keywords: powershell,cmdlet
Locale: en-US
Module Guid: 4ae9fd46-338a-459c-8186-07f910774cb8
Module Name: PackageManagement
ms.date: 06/09/2017
schema: 2.0.0
title: PackageManagement
ms.openlocfilehash: 88dcb47bee268af3553bb797aaa264e27ed8c51c
ms.sourcegitcommit: 22c93550c87af30c4895fcb9e9dd65e30d60ada0
ms.translationtype: MT
ms.contentlocale: nl-NL
ms.lasthandoff: 11/19/2020
ms.locfileid: "94889637"
---
# <span data-ttu-id="19707-103">Package management-module</span><span class="sxs-lookup"><span data-stu-id="19707-103">PackageManagement Module</span></span>

## <span data-ttu-id="19707-104">Description</span><span class="sxs-lookup"><span data-stu-id="19707-104">Description</span></span>

<span data-ttu-id="19707-105">In dit onderwerp vindt u Help-onderwerpen voor de Package Management-cmdlets.</span><span class="sxs-lookup"><span data-stu-id="19707-105">This topic displays help topics for the Package Management Cmdlets.</span></span>

> [!IMPORTANT]
> <span data-ttu-id="19707-106">Vanaf april 2020 biedt de PowerShell Gallery niet langer ondersteuning voor Transport Layer Security (TLS) versie 1,0 en 1,1.</span><span class="sxs-lookup"><span data-stu-id="19707-106">As of April 2020, the PowerShell Gallery no longer supports Transport Layer Security (TLS) versions 1.0 and 1.1.</span></span> <span data-ttu-id="19707-107">Als u geen TLS 1,2 of hoger gebruikt, wordt er een fout bericht weer gegeven wanneer u probeert toegang te krijgen tot de PowerShell Gallery.</span><span class="sxs-lookup"><span data-stu-id="19707-107">If you are not using TLS 1.2 or higher, you will receive an error when trying to access the PowerShell Gallery.</span></span> <span data-ttu-id="19707-108">Gebruik de volgende opdracht om ervoor te zorgen dat u TLS 1,2 gebruikt:</span><span class="sxs-lookup"><span data-stu-id="19707-108">Use the following command to ensure you are using TLS 1.2:</span></span>
>
> `[Net.ServicePointManager]::SecurityProtocol = [Net.SecurityProtocolType]::Tls12`
>
> <span data-ttu-id="19707-109">Zie de [aankondiging](https://devblogs.microsoft.com/powershell/powershell-gallery-tls-support/) in het Power shell-blog voor meer informatie.</span><span class="sxs-lookup"><span data-stu-id="19707-109">For more information, see the [announcement](https://devblogs.microsoft.com/powershell/powershell-gallery-tls-support/) in the PowerShell blog.</span></span>

## <span data-ttu-id="19707-110">PackageManagement-cmdlets</span><span class="sxs-lookup"><span data-stu-id="19707-110">PackageManagement Cmdlets</span></span>

### [<span data-ttu-id="19707-111">Zoeken-pakket</span><span class="sxs-lookup"><span data-stu-id="19707-111">Find-Package</span></span>](Find-Package.md)
<span data-ttu-id="19707-112">Zoekt naar software pakketten in beschik bare pakket bronnen.</span><span class="sxs-lookup"><span data-stu-id="19707-112">Finds software packages in available package sources.</span></span>

### [<span data-ttu-id="19707-113">Zoeken-package provider</span><span class="sxs-lookup"><span data-stu-id="19707-113">Find-PackageProvider</span></span>](Find-PackageProvider.md)
<span data-ttu-id="19707-114">Retourneert een lijst met pakket beheer pakket providers die beschikbaar zijn voor installatie.</span><span class="sxs-lookup"><span data-stu-id="19707-114">Returns a list of Package Management package providers available for installation.</span></span>

### [<span data-ttu-id="19707-115">Get-Package</span><span class="sxs-lookup"><span data-stu-id="19707-115">Get-Package</span></span>](Get-Package.md)
<span data-ttu-id="19707-116">Retourneert een lijst met alle software pakketten die zijn geïnstalleerd met **Package Management**.</span><span class="sxs-lookup"><span data-stu-id="19707-116">Returns a list of all software packages that were installed with **PackageManagement**.</span></span>

### [<span data-ttu-id="19707-117">Get-PackageProvider</span><span class="sxs-lookup"><span data-stu-id="19707-117">Get-PackageProvider</span></span>](Get-PackageProvider.md)
<span data-ttu-id="19707-118">Retourneert een lijst met pakket providers die zijn verbonden met pakket beheer.</span><span class="sxs-lookup"><span data-stu-id="19707-118">Returns a list of package providers that are connected to Package Management.</span></span>

### [<span data-ttu-id="19707-119">Get-PackageSource</span><span class="sxs-lookup"><span data-stu-id="19707-119">Get-PackageSource</span></span>](Get-PackageSource.md)
<span data-ttu-id="19707-120">Hiermee wordt een lijst opgehaald met pakket bronnen die zijn geregistreerd voor een pakket provider.</span><span class="sxs-lookup"><span data-stu-id="19707-120">Gets a list of package sources that are registered for a package provider.</span></span>

### [<span data-ttu-id="19707-121">Import-package provider</span><span class="sxs-lookup"><span data-stu-id="19707-121">Import-PackageProvider</span></span>](Import-PackageProvider.md)
<span data-ttu-id="19707-122">Voegt pakket beheer pakket providers toe aan de huidige sessie.</span><span class="sxs-lookup"><span data-stu-id="19707-122">Adds Package Management package providers to the current session.</span></span>

### [<span data-ttu-id="19707-123">Install-Package</span><span class="sxs-lookup"><span data-stu-id="19707-123">Install-Package</span></span>](Install-Package.md)
<span data-ttu-id="19707-124">Hiermee worden een of meer software pakketten geïnstalleerd.</span><span class="sxs-lookup"><span data-stu-id="19707-124">Installs one or more software packages.</span></span>

### [<span data-ttu-id="19707-125">Install-package provider</span><span class="sxs-lookup"><span data-stu-id="19707-125">Install-PackageProvider</span></span>](Install-PackageProvider.md)
<span data-ttu-id="19707-126">Hiermee worden een of meer pakket beheer pakket providers geïnstalleerd.</span><span class="sxs-lookup"><span data-stu-id="19707-126">Installs one or more Package Management package providers.</span></span>

### [<span data-ttu-id="19707-127">REGI ster-PackageSource</span><span class="sxs-lookup"><span data-stu-id="19707-127">Register-PackageSource</span></span>](Register-PackageSource.md)
<span data-ttu-id="19707-128">Hiermee voegt u een pakket bron voor een opgegeven pakket provider toe.</span><span class="sxs-lookup"><span data-stu-id="19707-128">Adds a package source for a specified package provider.</span></span>

### [<span data-ttu-id="19707-129">Opslaan-pakket</span><span class="sxs-lookup"><span data-stu-id="19707-129">Save-Package</span></span>](Save-Package.md)
<span data-ttu-id="19707-130">Hiermee worden pakketten op de lokale computer opgeslagen zonder dat ze worden geïnstalleerd.</span><span class="sxs-lookup"><span data-stu-id="19707-130">Saves packages to the local computer without installing them.</span></span>

### [<span data-ttu-id="19707-131">Set-PackageSource</span><span class="sxs-lookup"><span data-stu-id="19707-131">Set-PackageSource</span></span>](Set-PackageSource.md)
<span data-ttu-id="19707-132">Vervangt een pakket bron voor een opgegeven pakket provider.</span><span class="sxs-lookup"><span data-stu-id="19707-132">Replaces a package source for a specified package provider.</span></span>

### [<span data-ttu-id="19707-133">Uninstall-pakket</span><span class="sxs-lookup"><span data-stu-id="19707-133">Uninstall-Package</span></span>](Uninstall-Package.md)
<span data-ttu-id="19707-134">Hiermee verwijdert u een of meer software pakketten.</span><span class="sxs-lookup"><span data-stu-id="19707-134">Uninstalls one or more software packages.</span></span>

### [<span data-ttu-id="19707-135">Registratie ongedaan maken-PackageSource</span><span class="sxs-lookup"><span data-stu-id="19707-135">Unregister-PackageSource</span></span>](Unregister-PackageSource.md)
<span data-ttu-id="19707-136">Hiermee verwijdert u een geregistreerde pakket bron.</span><span class="sxs-lookup"><span data-stu-id="19707-136">Removes a registered package source.</span></span>

