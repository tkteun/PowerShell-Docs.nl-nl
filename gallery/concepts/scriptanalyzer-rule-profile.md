---
ms.date: 06/12/2017
contributor: JKeithB
keywords: Galerie, powershell, cmdlet, psgallery
title: ScriptAnalyzer regel profiel voor galerie
ms.openlocfilehash: 939f01dece56b283dbe6e03c888f42ff866707af
ms.sourcegitcommit: caac7d098a448232304c9d6728e7340ec7517a71
ms.translationtype: MT
ms.contentlocale: nl-NL
ms.lasthandoff: 03/16/2019
ms.locfileid: "58059589"
---
# <a name="scriptanalyzer-rule-profile-for-gallery"></a><span data-ttu-id="49814-103">ScriptAnalyzer regel profiel voor galerie</span><span class="sxs-lookup"><span data-stu-id="49814-103">ScriptAnalyzer rule profile for Gallery</span></span>

<span data-ttu-id="49814-104">Om ervoor te zorgen de kwaliteit van de pakketten die zijn gepubliceerd naar de PowerShell Gallery, voeren we [PSScriptAnalyzer](https://github.com/PowerShell/PSScriptAnalyzer) regels om te bepalen of er eventuele schendingen in de scripts die zijn verzonden.</span><span class="sxs-lookup"><span data-stu-id="49814-104">To ensure the quality of packages published to PowerShell Gallery, we run [PSScriptAnalyzer](https://github.com/PowerShell/PSScriptAnalyzer) rules to determine if there are any violations in the scripts submitted.</span></span>

<span data-ttu-id="49814-105">U vindt de lijst met regels die wordt uitgevoerd op ScriptAnalyzer [GitHub-pagina](https://github.com/PowerShell/PSScriptAnalyzer/blob/development/Engine/Settings/PSGallery.psd1).</span><span class="sxs-lookup"><span data-stu-id="49814-105">You can find the list of rules we are running on ScriptAnalyzer [GitHub page](https://github.com/PowerShell/PSScriptAnalyzer/blob/development/Engine/Settings/PSGallery.psd1).</span></span>
<span data-ttu-id="49814-106">Neem contact op met de PowerShell Gallery-beheerders, hebt u vragen met betrekking tot de regels dat wordt uitgevoerd, of een probleem voor ScriptAnalyzer openen.</span><span class="sxs-lookup"><span data-stu-id="49814-106">If you have any concerns regarding the rules we are running, please contact PowerShell Gallery Administrators, or open an issue for ScriptAnalyzer.</span></span>

<span data-ttu-id="49814-107">ScriptAnalyzer resultaten wordt weergegeven op elke pakketpagina afzonderlijke in de galerie in de komende release.</span><span class="sxs-lookup"><span data-stu-id="49814-107">ScriptAnalyzer results will be displayed on each individual package page in Gallery in the coming release.</span></span> <span data-ttu-id="49814-108">Het wordt aangeraden de eigenaren van het pakket om te controleren op hun pakketten om te controleren of dat er zijn geen ernstige fouten in de gepubliceerde pakketten.</span><span class="sxs-lookup"><span data-stu-id="49814-108">We encourage package owners to check their packages to make sure there are no severe errors in published packages.</span></span>
