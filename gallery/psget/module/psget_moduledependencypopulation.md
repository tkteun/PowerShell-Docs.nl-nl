---
ms.date: 2017-06-12
contributor: manikb
ms.topic: reference
keywords: Galerie, powershell, cmdlet, psget
title: psget_moduledependencypopulation
ms.openlocfilehash: 126cd65ac35a31f4118474bc36dac1836ec0f22e
ms.sourcegitcommit: 75f70c7df01eea5e7a2c16f9a3ab1dd437a1f8fd
ms.translationtype: MT
ms.contentlocale: nl-NL
ms.lasthandoff: 06/12/2017
---
# <a name="logic-for-preparing-the-module-dependencies-during-publish-operation"></a>Logica voor het voorbereiden van de module afhankelijkheden tijdens publicatiebewerking
1.  Modules die worden vermeld als deel van RequiredModules worden beschouwd als afhankelijkheden.
2.  Modules die worden vermeld als deel van NestedModules, waarvan base module bevindt zich niet onder de opgegeven module base, worden beschouwd als afhankelijkheden.

3.  Hierboven afhankelijkheden moet beschikbaar zijn in de doelopslagplaats met hetzelfde, anders publiceren bewerking leidt tot een fout opgetreden.
    Bijvoorbeeld: als 'SnippetPx' niet beschikbaar in de opslagplaats is, hieronder fout gegenereerd.
    ```powershell
    Publish-PSArtifactUtility : PowerShellGet cannot resolve the module dependency 'SnippetPx' of the module 'TypePx' on the repository 'LocalRepo'. Verify that the dependent module 'SnippetPx' is available in the repository 'LocalRepo'. If this dependent
    'SnippetPx' is managed externally, add it to the ExternalModuleDependencies entry in the PSData section of the module manifest.
    ```
4.  Enkele afhankelijkheden module extern kunnen worden beheerd, in dat geval ze moeten worden toegevoegd aan de vermelding ExternalModuleDependencies in de sectie PSData van de module-manifest.
    Hieronder onderdeel in het bovenstaande foutbericht
    ```powershell
    If this dependent 'SnippetPx' is managed externally, add it to the ExternalModuleDependencies entry in the PSData section of the module manifest.
    ```

*Tijdens de installatie van de beleidsmodule hierboven voorbereide afhankelijkheden wordt lijst gebruikt voor het installeren van de afhankelijkheden.*

*Zorg ervoor dat uw module afhankelijkheden beschikbaar onder $env zijn: PSModulePath op uw systeem tijdens de bewerking publiceren.*

