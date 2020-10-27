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
# <a name="scriptanalyzer-rule-profile-for-gallery"></a>ScriptAnalyzer-regel profiel voor de galerie

Om ervoor te zorgen dat de kwaliteit van de pakketten die worden gepubliceerd op PowerShell Gallery, voeren we [PSScriptAnalyzer](https://github.com/PowerShell/PSScriptAnalyzer) -regels uit om te bepalen of er schendingen zijn in de verzonden scripts.

U vindt de lijst met regels die worden uitgevoerd op de ScriptAnalyzer [github-pagina](https://github.com/PowerShell/PSScriptAnalyzer/blob/development/Engine/Settings/PSGallery.psd1).
Als u problemen hebt met betrekking tot de regels die worden uitgevoerd, neemt u contact op met PowerShell Gallery-beheerders of opent u een probleem voor ScriptAnalyzer.

ScriptAnalyzer resultaten worden weer gegeven op elke afzonderlijke pakket pagina in de galerie in de volgende release. We moedigen pakket eigenaren aan om hun pakketten te controleren om ervoor te zorgen dat er geen ernstige fouten in gepubliceerde pakketten zijn.
