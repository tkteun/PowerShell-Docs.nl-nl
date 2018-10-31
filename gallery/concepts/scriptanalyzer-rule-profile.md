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
# <a name="scriptanalyzer-rule-profile-for-gallery"></a>ScriptAnalyzer regel profiel voor galerie

Om ervoor te zorgen de kwaliteit van de pakketten die zijn gepubliceerd naar de PowerShell Gallery, voeren we [PSScriptAnalyzer](https://github.com/PowerShell/PSScriptAnalyzer) regels om te bepalen of er eventuele schendingen in de scripts die zijn verzonden.

U vindt de lijst met regels die wordt uitgevoerd op ScriptAnalyzer [GitHub-pagina](https://github.com/PowerShell/PSScriptAnalyzer/blob/development/Engine/Settings/PSGallery.psd1).
Neem contact op met de PowerShell Gallery-beheerders, hebt u vragen met betrekking tot de regels dat wordt uitgevoerd, of een probleem voor ScriptAnalzyer openen.

ScriptAnalyzer resultaten wordt weergegeven op elke pakketpagina afzonderlijke in de galerie in de komende release. Het wordt aangeraden de eigenaren van het pakket om te controleren op hun pakketten om te controleren of dat er zijn geen ernstige fouten in de gepubliceerde pakketten.
