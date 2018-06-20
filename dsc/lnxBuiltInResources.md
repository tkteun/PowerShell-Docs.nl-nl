---
ms.date: 06/12/2017
keywords: DSC, powershell, configuratie, setup
title: Ingebouwde Desired State Configuration Resources voor Linux
ms.openlocfilehash: ea700d24c7ff4377af671944184abb3f201852e8
ms.sourcegitcommit: 54534635eedacf531d8d6344019dc16a50b8b441
ms.translationtype: MT
ms.contentlocale: nl-NL
ms.lasthandoff: 05/17/2018
ms.locfileid: "34218498"
---
# <a name="built-in-desired-state-configuration-resources-for-linux"></a><span data-ttu-id="17850-103">Ingebouwde Desired State Configuration Resources voor Linux</span><span class="sxs-lookup"><span data-stu-id="17850-103">Built-In Desired State Configuration Resources for Linux</span></span>

<span data-ttu-id="17850-104">Resources zijn bouwstenen die u gebruiken kunt om een script PowerShell Desired State Configuration (DSC) te schrijven.</span><span class="sxs-lookup"><span data-stu-id="17850-104">Resources are building blocks that you can use to write a PowerShell Desired State Configuration (DSC) script.</span></span> <span data-ttu-id="17850-105">DSC voor Linux wordt geleverd met een set ingebouwde functionaliteit voor het configureren van resources, zoals bestanden en mappen, pakketten, omgevingsvariabelen en services en processen.</span><span class="sxs-lookup"><span data-stu-id="17850-105">DSC for Linux comes with a set of built-in functionality for configuring resources such as files and folders, packages, environment variables, and services and processes.</span></span>

## <a name="built-in-resources"></a><span data-ttu-id="17850-106">Ingebouwde resources</span><span class="sxs-lookup"><span data-stu-id="17850-106">Built-in resources</span></span>

<span data-ttu-id="17850-107">De volgende tabel bevat een lijst van deze resources en koppelingen naar onderwerpen waarin ze in detail beschreven.</span><span class="sxs-lookup"><span data-stu-id="17850-107">The following table provides a list of these resources and links to topics that describe them in detail.</span></span>

* <span data-ttu-id="17850-108">[nxArchive Resource](lnxArchiveResource.md)--biedt een mechanisme voor het uitpakken van bestanden te archiveren (tar, .zip) op een specifiek pad.</span><span class="sxs-lookup"><span data-stu-id="17850-108">[nxArchive Resource](lnxArchiveResource.md)--Provides a mechanism to unpack archive (.tar, .zip) files at a specific path.</span></span>
* <span data-ttu-id="17850-109">[nxEnvironment Resource](lnxEnvironmentResource.md)--omgevingsvariabelen op doelknooppunten beheert.</span><span class="sxs-lookup"><span data-stu-id="17850-109">[nxEnvironment Resource](lnxEnvironmentResource.md)--Manages environment variables on target nodes.</span></span>
* <span data-ttu-id="17850-110">[nxFile Resource](lnxFileResource.md)--Linux beheert bestanden en mappen.</span><span class="sxs-lookup"><span data-stu-id="17850-110">[nxFile Resource](lnxFileResource.md)--Manages Linux files and directories.</span></span>
* <span data-ttu-id="17850-111">[nxFileLine Resource](lnxFileLineResource.md)--beheert afzonderlijke regels in een Linux-bestand.</span><span class="sxs-lookup"><span data-stu-id="17850-111">[nxFileLine Resource](lnxFileLineResource.md)--Manages individual lines in a Linux file.</span></span>
* <span data-ttu-id="17850-112">[nxGroup Resource](lnxGroupResource.md)--beheert lokale Linux-groepen.</span><span class="sxs-lookup"><span data-stu-id="17850-112">[nxGroup Resource](lnxGroupResource.md)--Manages local Linux groups.</span></span>
* <span data-ttu-id="17850-113">[nxPackage Resource](lnxPackageResource.md)--beheert pakketten op Linux-knooppunten.</span><span class="sxs-lookup"><span data-stu-id="17850-113">[nxPackage Resource](lnxPackageResource.md)--Manages packages on Linux nodes.</span></span>
* <span data-ttu-id="17850-114">[nxScript Resource](lnxScriptResource.md)--scripts op de doelknooppunten wordt uitgevoerd.</span><span class="sxs-lookup"><span data-stu-id="17850-114">[nxScript Resource](lnxScriptResource.md)--Runs scripts on target nodes.</span></span>
* <span data-ttu-id="17850-115">[nxService Resource](lnxServiceResource.md)--beheert Linux-services (daemons).</span><span class="sxs-lookup"><span data-stu-id="17850-115">[nxService Resource](lnxServiceResource.md)--Manages Linux services (daemons).</span></span>
* <span data-ttu-id="17850-116">[nxSshAuthorizedKeys Resource](lnxSshAuthorizedKeysResource.md)--beheert openbare ssh-sleutels voor een Linux-gebruiker.</span><span class="sxs-lookup"><span data-stu-id="17850-116">[nxSshAuthorizedKeys Resource](lnxSshAuthorizedKeysResource.md)--Manages public ssh keys for a Linux user.</span></span>
* <span data-ttu-id="17850-117">[nxUser Resource](lnxUserResource.md)--lokale Linux-gebruikers beheert.</span><span class="sxs-lookup"><span data-stu-id="17850-117">[nxUser Resource](lnxUserResource.md)--Manages local Linux users.</span></span>