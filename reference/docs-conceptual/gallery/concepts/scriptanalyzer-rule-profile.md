---
ms.date: 06/12/2017
contributor: JKeithB
keywords: Galerie, Power shell, cmdlet, psgallery
title: ScriptAnalyzer-regel profiel voor de galerie
ms.openlocfilehash: 939f01dece56b283dbe6e03c888f42ff866707af
ms.sourcegitcommit: 4a2cf30351620a58ba95ff5d76b247e601907589
ms.translationtype: MT
ms.contentlocale: nl-NL
ms.lasthandoff: 09/27/2019
ms.locfileid: "71329167"
---
# <a name="scriptanalyzer-rule-profile-for-gallery"></a><span data-ttu-id="579c2-103">ScriptAnalyzer-regel profiel voor de galerie</span><span class="sxs-lookup"><span data-stu-id="579c2-103">ScriptAnalyzer rule profile for Gallery</span></span>

<span data-ttu-id="579c2-104">Om ervoor te zorgen dat de kwaliteit van de pakketten die worden gepubliceerd op PowerShell Gallery, voeren we [PSScriptAnalyzer](https://github.com/PowerShell/PSScriptAnalyzer) -regels uit om te bepalen of er schendingen zijn in de verzonden scripts.</span><span class="sxs-lookup"><span data-stu-id="579c2-104">To ensure the quality of packages published to PowerShell Gallery, we run [PSScriptAnalyzer](https://github.com/PowerShell/PSScriptAnalyzer) rules to determine if there are any violations in the scripts submitted.</span></span>

<span data-ttu-id="579c2-105">U vindt de lijst met regels die worden uitgevoerd op de ScriptAnalyzer [github-pagina](https://github.com/PowerShell/PSScriptAnalyzer/blob/development/Engine/Settings/PSGallery.psd1).</span><span class="sxs-lookup"><span data-stu-id="579c2-105">You can find the list of rules we are running on ScriptAnalyzer [GitHub page](https://github.com/PowerShell/PSScriptAnalyzer/blob/development/Engine/Settings/PSGallery.psd1).</span></span>
<span data-ttu-id="579c2-106">Als u problemen hebt met betrekking tot de regels die worden uitgevoerd, neemt u contact op met PowerShell Gallery-beheerders of opent u een probleem voor ScriptAnalyzer.</span><span class="sxs-lookup"><span data-stu-id="579c2-106">If you have any concerns regarding the rules we are running, please contact PowerShell Gallery Administrators, or open an issue for ScriptAnalyzer.</span></span>

<span data-ttu-id="579c2-107">ScriptAnalyzer resultaten worden weer gegeven op elke afzonderlijke pakket pagina in de galerie in de volgende release.</span><span class="sxs-lookup"><span data-stu-id="579c2-107">ScriptAnalyzer results will be displayed on each individual package page in Gallery in the coming release.</span></span> <span data-ttu-id="579c2-108">We moedigen pakket eigenaren aan om hun pakketten te controleren om ervoor te zorgen dat er geen ernstige fouten in gepubliceerde pakketten zijn.</span><span class="sxs-lookup"><span data-stu-id="579c2-108">We encourage package owners to check their packages to make sure there are no severe errors in published packages.</span></span>
