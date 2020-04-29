---
ms.date: 06/12/2017
contributor: JKeithB
keywords: Galerie, Power shell, cmdlet, psgallery
title: ScriptAnalyzer-regel profiel voor de galerie
ms.openlocfilehash: 939f01dece56b283dbe6e03c888f42ff866707af
ms.sourcegitcommit: 6545c60578f7745be015111052fd7769f8289296
ms.translationtype: MT
ms.contentlocale: nl-NL
ms.lasthandoff: 04/22/2020
ms.locfileid: "71329167"
---
# <a name="scriptanalyzer-rule-profile-for-gallery"></a>ScriptAnalyzer-regel profiel voor de galerie

Om ervoor te zorgen dat de kwaliteit van de pakketten die worden gepubliceerd op PowerShell Gallery, voeren we [PSScriptAnalyzer](https://github.com/PowerShell/PSScriptAnalyzer) -regels uit om te bepalen of er schendingen zijn in de verzonden scripts.

U vindt de lijst met regels die worden uitgevoerd op de ScriptAnalyzer [github-pagina](https://github.com/PowerShell/PSScriptAnalyzer/blob/development/Engine/Settings/PSGallery.psd1).
Als u problemen hebt met betrekking tot de regels die worden uitgevoerd, neemt u contact op met PowerShell Gallery-beheerders of opent u een probleem voor ScriptAnalyzer.

ScriptAnalyzer resultaten worden weer gegeven op elke afzonderlijke pakket pagina in de galerie in de volgende release. We moedigen pakket eigenaren aan om hun pakketten te controleren om ervoor te zorgen dat er geen ernstige fouten in gepubliceerde pakketten zijn.
