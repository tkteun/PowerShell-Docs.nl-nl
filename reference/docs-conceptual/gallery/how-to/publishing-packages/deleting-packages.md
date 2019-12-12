---
ms.date: 06/12/2017
contributor: JKeithB
keywords: Galerie, Power shell, cmdlet, psgallery
title: Pakketten verwijderen
ms.openlocfilehash: 6bfb43b95e51d38bd606198cb8d2d9af0aa0be1e
ms.sourcegitcommit: debd2b38fb8070a7357bf1a4bf9cc736f3702f31
ms.translationtype: MT
ms.contentlocale: nl-NL
ms.lasthandoff: 12/05/2019
ms.locfileid: "71328789"
---
# <a name="deleting-packages"></a><span data-ttu-id="91700-103">Pakketten verwijderen</span><span class="sxs-lookup"><span data-stu-id="91700-103">Deleting Packages</span></span>

<span data-ttu-id="91700-104">De PowerShell Gallery biedt geen ondersteuning voor het permanent verwijderen van pakketten, omdat hierdoor iedereen die afhankelijk is van de beschik bare hoeveelheid, wordt verbroken.</span><span class="sxs-lookup"><span data-stu-id="91700-104">The PowerShell Gallery does not support permanent deletion of packages, because that would break anyone who is depending on it remaining available.</span></span>

<span data-ttu-id="91700-105">In plaats daarvan ondersteunt de PowerShell Gallery een manier om de lijst van een pakket op te zeggen, dat kan worden uitgevoerd op de pagina pakket beheer op de website.</span><span class="sxs-lookup"><span data-stu-id="91700-105">Instead, the PowerShell Gallery supports a way to 'unlist' a package, which can be done in the package management page on the web site.</span></span>
<span data-ttu-id="91700-106">Wanneer een pakket niet is vermeld, wordt het niet meer weer gegeven in de zoek opdracht en in een pakket vermelding, zowel op de PowerShell Gallery als met PowerShellGet-opdrachten.</span><span class="sxs-lookup"><span data-stu-id="91700-106">When a package is unlisted, it no longer shows up in search and in any package listing, both on the PowerShell Gallery and using PowerShellGet commands.</span></span>
<span data-ttu-id="91700-107">Het kan echter wel worden gedownload door de exacte versie op te geven. Dit houdt in dat de geautomatiseerde scripts blijven werken.</span><span class="sxs-lookup"><span data-stu-id="91700-107">However, it remains downloadable by specifying its exact version, which is what allows the automated scripts to continue working.</span></span>

<span data-ttu-id="91700-108">Als u een uitzonderlijke situatie hebt waarbij een van uw pakketten moet worden verwijderd, kan dit hand matig worden verwerkt door het PowerShell Gallery team.</span><span class="sxs-lookup"><span data-stu-id="91700-108">If you run into an exceptional situation where you think one of your packages must be deleted, this can be handled manually by the PowerShell Gallery team.</span></span>
<span data-ttu-id="91700-109">Als er bijvoorbeeld sprake is van een inbreuk op het auteurs recht of mogelijk schadelijke inhoud, kan dit een geldige reden voor het verwijderen van het probleem zijn.</span><span class="sxs-lookup"><span data-stu-id="91700-109">For example, if there is a copyright infringement issue, or potentially harmful content, that could be a valid reason to delete it.</span></span>
<span data-ttu-id="91700-110">U moet in dat geval een ondersteunings aanvraag indienen via [PowerShell Gallery](https://www.PowerShellGallery.com) .</span><span class="sxs-lookup"><span data-stu-id="91700-110">You should submit a support request through [PowerShell Gallery](https://www.PowerShellGallery.com) in that case.</span></span>
