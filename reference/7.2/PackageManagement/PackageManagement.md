---
Download Help Link: https://aka.ms/powershell72-help
Help Version: 7.2.0.0
Locale: en-US
Module Guid: 4ae9fd46-338a-459c-8186-07f910774cb8
Module Name: PackageManagement
ms.date: 06/09/2017
schema: 2.0.0
title: PackageManagement
ms.openlocfilehash: 86e6f37f6f7f0527c5dcca309cf581cb6f1b4de5
ms.sourcegitcommit: 22c93550c87af30c4895fcb9e9dd65e30d60ada0
ms.translationtype: MT
ms.contentlocale: nl-NL
ms.lasthandoff: 11/19/2020
ms.locfileid: "94889329"
---
# <span data-ttu-id="77caf-102">Package management-module</span><span class="sxs-lookup"><span data-stu-id="77caf-102">PackageManagement Module</span></span>

## <span data-ttu-id="77caf-103">Description</span><span class="sxs-lookup"><span data-stu-id="77caf-103">Description</span></span>

<span data-ttu-id="77caf-104">In dit onderwerp vindt u Help-onderwerpen voor de Package Management-cmdlets.</span><span class="sxs-lookup"><span data-stu-id="77caf-104">This topic displays help topics for the Package Management Cmdlets.</span></span>

> [!IMPORTANT]
> <span data-ttu-id="77caf-105">Vanaf april 2020 biedt de PowerShell Gallery niet langer ondersteuning voor Transport Layer Security (TLS) versie 1,0 en 1,1.</span><span class="sxs-lookup"><span data-stu-id="77caf-105">As of April 2020, the PowerShell Gallery no longer supports Transport Layer Security (TLS) versions 1.0 and 1.1.</span></span> <span data-ttu-id="77caf-106">Als u geen TLS 1,2 of hoger gebruikt, wordt er een fout bericht weer gegeven wanneer u probeert toegang te krijgen tot de PowerShell Gallery.</span><span class="sxs-lookup"><span data-stu-id="77caf-106">If you are not using TLS 1.2 or higher, you will receive an error when trying to access the PowerShell Gallery.</span></span> <span data-ttu-id="77caf-107">Gebruik de volgende opdracht om ervoor te zorgen dat u TLS 1,2 gebruikt:</span><span class="sxs-lookup"><span data-stu-id="77caf-107">Use the following command to ensure you are using TLS 1.2:</span></span>
>
> `[Net.ServicePointManager]::SecurityProtocol = [Net.SecurityProtocolType]::Tls12`
>
> <span data-ttu-id="77caf-108">Zie de [aankondiging](https://devblogs.microsoft.com/powershell/powershell-gallery-tls-support/) in het Power shell-blog voor meer informatie.</span><span class="sxs-lookup"><span data-stu-id="77caf-108">For more information, see the [announcement](https://devblogs.microsoft.com/powershell/powershell-gallery-tls-support/) in the PowerShell blog.</span></span>

## <span data-ttu-id="77caf-109">PackageManagement-cmdlets</span><span class="sxs-lookup"><span data-stu-id="77caf-109">PackageManagement Cmdlets</span></span>

### [<span data-ttu-id="77caf-110">Zoeken-pakket</span><span class="sxs-lookup"><span data-stu-id="77caf-110">Find-Package</span></span>](Find-Package.md)
<span data-ttu-id="77caf-111">Zoekt naar software pakketten in beschik bare pakket bronnen.</span><span class="sxs-lookup"><span data-stu-id="77caf-111">Finds software packages in available package sources.</span></span>

### [<span data-ttu-id="77caf-112">Zoeken-package provider</span><span class="sxs-lookup"><span data-stu-id="77caf-112">Find-PackageProvider</span></span>](Find-PackageProvider.md)
<span data-ttu-id="77caf-113">Retourneert een lijst met pakket beheer pakket providers die beschikbaar zijn voor installatie.</span><span class="sxs-lookup"><span data-stu-id="77caf-113">Returns a list of Package Management package providers available for installation.</span></span>

### [<span data-ttu-id="77caf-114">Get-Package</span><span class="sxs-lookup"><span data-stu-id="77caf-114">Get-Package</span></span>](Get-Package.md)
<span data-ttu-id="77caf-115">Retourneert een lijst met alle software pakketten die zijn geïnstalleerd met **Package Management**.</span><span class="sxs-lookup"><span data-stu-id="77caf-115">Returns a list of all software packages that were installed with **PackageManagement**.</span></span>

### [<span data-ttu-id="77caf-116">Get-PackageProvider</span><span class="sxs-lookup"><span data-stu-id="77caf-116">Get-PackageProvider</span></span>](Get-PackageProvider.md)
<span data-ttu-id="77caf-117">Retourneert een lijst met pakket providers die zijn verbonden met pakket beheer.</span><span class="sxs-lookup"><span data-stu-id="77caf-117">Returns a list of package providers that are connected to Package Management.</span></span>

### [<span data-ttu-id="77caf-118">Get-PackageSource</span><span class="sxs-lookup"><span data-stu-id="77caf-118">Get-PackageSource</span></span>](Get-PackageSource.md)
<span data-ttu-id="77caf-119">Hiermee wordt een lijst opgehaald met pakket bronnen die zijn geregistreerd voor een pakket provider.</span><span class="sxs-lookup"><span data-stu-id="77caf-119">Gets a list of package sources that are registered for a package provider.</span></span>

### [<span data-ttu-id="77caf-120">Import-package provider</span><span class="sxs-lookup"><span data-stu-id="77caf-120">Import-PackageProvider</span></span>](Import-PackageProvider.md)
<span data-ttu-id="77caf-121">Voegt pakket beheer pakket providers toe aan de huidige sessie.</span><span class="sxs-lookup"><span data-stu-id="77caf-121">Adds Package Management package providers to the current session.</span></span>

### [<span data-ttu-id="77caf-122">Install-Package</span><span class="sxs-lookup"><span data-stu-id="77caf-122">Install-Package</span></span>](Install-Package.md)
<span data-ttu-id="77caf-123">Hiermee worden een of meer software pakketten geïnstalleerd.</span><span class="sxs-lookup"><span data-stu-id="77caf-123">Installs one or more software packages.</span></span>

### [<span data-ttu-id="77caf-124">Install-package provider</span><span class="sxs-lookup"><span data-stu-id="77caf-124">Install-PackageProvider</span></span>](Install-PackageProvider.md)
<span data-ttu-id="77caf-125">Hiermee worden een of meer pakket beheer pakket providers geïnstalleerd.</span><span class="sxs-lookup"><span data-stu-id="77caf-125">Installs one or more Package Management package providers.</span></span>

### [<span data-ttu-id="77caf-126">REGI ster-PackageSource</span><span class="sxs-lookup"><span data-stu-id="77caf-126">Register-PackageSource</span></span>](Register-PackageSource.md)
<span data-ttu-id="77caf-127">Hiermee voegt u een pakket bron voor een opgegeven pakket provider toe.</span><span class="sxs-lookup"><span data-stu-id="77caf-127">Adds a package source for a specified package provider.</span></span>

### [<span data-ttu-id="77caf-128">Opslaan-pakket</span><span class="sxs-lookup"><span data-stu-id="77caf-128">Save-Package</span></span>](Save-Package.md)
<span data-ttu-id="77caf-129">Hiermee worden pakketten op de lokale computer opgeslagen zonder dat ze worden geïnstalleerd.</span><span class="sxs-lookup"><span data-stu-id="77caf-129">Saves packages to the local computer without installing them.</span></span>

### [<span data-ttu-id="77caf-130">Set-PackageSource</span><span class="sxs-lookup"><span data-stu-id="77caf-130">Set-PackageSource</span></span>](Set-PackageSource.md)
<span data-ttu-id="77caf-131">Vervangt een pakket bron voor een opgegeven pakket provider.</span><span class="sxs-lookup"><span data-stu-id="77caf-131">Replaces a package source for a specified package provider.</span></span>

### [<span data-ttu-id="77caf-132">Uninstall-pakket</span><span class="sxs-lookup"><span data-stu-id="77caf-132">Uninstall-Package</span></span>](Uninstall-Package.md)
<span data-ttu-id="77caf-133">Hiermee verwijdert u een of meer software pakketten.</span><span class="sxs-lookup"><span data-stu-id="77caf-133">Uninstalls one or more software packages.</span></span>

### [<span data-ttu-id="77caf-134">Registratie ongedaan maken-PackageSource</span><span class="sxs-lookup"><span data-stu-id="77caf-134">Unregister-PackageSource</span></span>](Unregister-PackageSource.md)
<span data-ttu-id="77caf-135">Hiermee verwijdert u een geregistreerde pakket bron.</span><span class="sxs-lookup"><span data-stu-id="77caf-135">Removes a registered package source.</span></span>
