---
ms.date: 06/12/2017
title: ScriptAnalyzer-regel profiel voor de galerie
description: Hierin wordt uitgelegd hoe de Power shell-ScriptAnalyzer is geïntegreerd met de PowerShell Gallery.
ms.openlocfilehash: 3af710e8811f0fabfb02f5317d5b4ff9c320f29a
ms.sourcegitcommit: 488a940c7c828820b36a6ba56c119f64614afc29
ms.translationtype: MT
ms.contentlocale: nl-NL
ms.lasthandoff: 10/27/2020
ms.locfileid: "92646761"
---
# <a name="scriptanalyzer-rule-profile-for-gallery"></a><span data-ttu-id="738d8-103">ScriptAnalyzer-regel profiel voor de galerie</span><span class="sxs-lookup"><span data-stu-id="738d8-103">ScriptAnalyzer rule profile for Gallery</span></span>

<span data-ttu-id="738d8-104">Om ervoor te zorgen dat de kwaliteit van de pakketten die worden gepubliceerd op PowerShell Gallery, voeren we [PSScriptAnalyzer](https://github.com/PowerShell/PSScriptAnalyzer) -regels uit om te bepalen of er schendingen zijn in de verzonden scripts.</span><span class="sxs-lookup"><span data-stu-id="738d8-104">To ensure the quality of packages published to PowerShell Gallery, we run [PSScriptAnalyzer](https://github.com/PowerShell/PSScriptAnalyzer) rules to determine if there are any violations in the scripts submitted.</span></span>

<span data-ttu-id="738d8-105">U vindt de lijst met regels die worden uitgevoerd op de ScriptAnalyzer [github-pagina](https://github.com/PowerShell/PSScriptAnalyzer/blob/development/Engine/Settings/PSGallery.psd1).</span><span class="sxs-lookup"><span data-stu-id="738d8-105">You can find the list of rules we are running on ScriptAnalyzer [GitHub page](https://github.com/PowerShell/PSScriptAnalyzer/blob/development/Engine/Settings/PSGallery.psd1).</span></span>
<span data-ttu-id="738d8-106">Als u problemen hebt met betrekking tot de regels die worden uitgevoerd, neemt u contact op met PowerShell Gallery-beheerders of opent u een probleem voor ScriptAnalyzer.</span><span class="sxs-lookup"><span data-stu-id="738d8-106">If you have any concerns regarding the rules we are running, please contact PowerShell Gallery Administrators, or open an issue for ScriptAnalyzer.</span></span>

<span data-ttu-id="738d8-107">ScriptAnalyzer resultaten worden weer gegeven op elke afzonderlijke pakket pagina in de galerie in de volgende release.</span><span class="sxs-lookup"><span data-stu-id="738d8-107">ScriptAnalyzer results will be displayed on each individual package page in Gallery in the coming release.</span></span> <span data-ttu-id="738d8-108">We moedigen pakket eigenaren aan om hun pakketten te controleren om ervoor te zorgen dat er geen ernstige fouten in gepubliceerde pakketten zijn.</span><span class="sxs-lookup"><span data-stu-id="738d8-108">We encourage package owners to check their packages to make sure there are no severe errors in published packages.</span></span>
