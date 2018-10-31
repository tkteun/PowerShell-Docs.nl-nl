---
ms.date: 06/12/2017
contributor: JKeithB
keywords: Galerie, powershell, cmdlet, psgallery
title: ScriptAnalyzer regel profiel voor galerie
ms.openlocfilehash: d91a88981cc2f3269a1f8b6ee864f8333a2f097c
ms.sourcegitcommit: 98b7cfd8ad5718efa8e320526ca76c3cc4141d78
ms.translationtype: MT
ms.contentlocale: nl-NL
ms.lasthandoff: 10/25/2018
ms.locfileid: "50002493"
---
# <a name="scriptanalyzer-rule-profile-for-gallery"></a><span data-ttu-id="31d5d-103">ScriptAnalyzer regel profiel voor galerie</span><span class="sxs-lookup"><span data-stu-id="31d5d-103">ScriptAnalyzer rule profile for Gallery</span></span>

<span data-ttu-id="31d5d-104">Om ervoor te zorgen de kwaliteit van de pakketten die zijn gepubliceerd naar de PowerShell Gallery, voeren we [PSScriptAnalyzer](https://github.com/PowerShell/PSScriptAnalyzer) regels om te bepalen of er eventuele schendingen in de scripts die zijn verzonden.</span><span class="sxs-lookup"><span data-stu-id="31d5d-104">To ensure the quality of packages published to PowerShell Gallery, we run [PSScriptAnalyzer](https://github.com/PowerShell/PSScriptAnalyzer) rules to determine if there are any violations in the scripts submitted.</span></span>

<span data-ttu-id="31d5d-105">U vindt de lijst met regels die wordt uitgevoerd op ScriptAnalyzer [GitHub-pagina](https://github.com/PowerShell/PSScriptAnalyzer/blob/development/Engine/Settings/PSGallery.psd1).</span><span class="sxs-lookup"><span data-stu-id="31d5d-105">You can find the list of rules we are running on ScriptAnalyzer [GitHub page](https://github.com/PowerShell/PSScriptAnalyzer/blob/development/Engine/Settings/PSGallery.psd1).</span></span>
<span data-ttu-id="31d5d-106">Neem contact op met de PowerShell Gallery-beheerders, hebt u vragen met betrekking tot de regels dat wordt uitgevoerd, of een probleem voor ScriptAnalzyer openen.</span><span class="sxs-lookup"><span data-stu-id="31d5d-106">If you have any concerns regarding the rules we are running, please contact PowerShell Gallery Administrators, or open an issue for ScriptAnalzyer.</span></span>

<span data-ttu-id="31d5d-107">ScriptAnalyzer resultaten wordt weergegeven op elke pakketpagina afzonderlijke in de galerie in de komende release.</span><span class="sxs-lookup"><span data-stu-id="31d5d-107">ScriptAnalyzer results will be displayed on each individual package page in Gallery in the coming release.</span></span> <span data-ttu-id="31d5d-108">Het wordt aangeraden de eigenaren van het pakket om te controleren op hun pakketten om te controleren of dat er zijn geen ernstige fouten in de gepubliceerde pakketten.</span><span class="sxs-lookup"><span data-stu-id="31d5d-108">We encourage package owners to check their packages to make sure there are no severe errors in published packages.</span></span>
