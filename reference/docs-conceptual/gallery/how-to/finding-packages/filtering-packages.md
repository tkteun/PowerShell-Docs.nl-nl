---
ms.date: 06/12/2017
title: Zoek resultaten filteren
description: In dit artikel wordt de gebruikers interface beschreven waarmee inhoud in het PowerShell Gallery wordt gefilterd.
ms.openlocfilehash: cc375f3ddb35c95ed134776500bd326bc3db6b1a
ms.sourcegitcommit: 488a940c7c828820b36a6ba56c119f64614afc29
ms.translationtype: MT
ms.contentlocale: nl-NL
ms.lasthandoff: 10/27/2020
ms.locfileid: "92661405"
---
# <a name="filtering-search-results"></a>Zoek resultaten filteren

Op het [tabblad pakketten](https://www.powershellgallery.com/packages) worden alle beschik bare pakketten weer gegeven in de PowerShell Gallery.

Er zijn verschillende manieren waarop u de pakketten kunt filteren, sorteren en doorzoeken. Klik op het pakket voor meer informatie over een bepaald pakket.

## <a name="filter-by"></a>Filteren op

De vervolg keuzelijst onder filteren op staat gebruikers toe om de resultaten te filteren op:

- Voorlopige versie toevoegen
- Alleen stabiel

Zie [prerelease-versie die is toegevoegd aan PowerShellGet en PowerShell Gallery](https://blogs.msdn.microsoft.com/powershell/2017/12/05/prerelease-versioning-added-to-powershellget-and-powershell-gallery/) in het Power shell-team blog voor meer informatie over ' Prerelease ' en ' stabiele '.

Met de selectie vakjes in de vervolg keuzelijst kunnen gebruikers de resultaten filteren door:

- Pakket typen
  - Module
  - Script
- Categorieën
  - Cmdlet
  - DSC-resource
  - Functie
  - Functie mogelijkheid
  - Werkstroom

Als u alleen modules in de PowerShell Gallery wilt weer geven, controleert u module in de pakket typen. Als u alleen scripts wilt weer geven in de PowerShell Gallery, controleert u het script in de pakket typen.

> [!NOTE]
> Filters zijn inclusief. Voor beeld: een pakket met cmdlets en functies wordt weer gegeven als de cmdlet of functie (of beide) is ingeschakeld. Als geen van beide is geselecteerd, wordt het pakket niet weer gegeven. Als alle categorieën zijn geselecteerd, worden alleen pakketten met een van deze categorieën weer gegeven. **Pakketten die geen deel uitmaken van een van deze categorieën, worden niet weer gegeven.**

## <a name="sort-by"></a>Sorteren op

Met de vervolg keuzelijst sorteren op kunnen gebruikers de resultaten sorteren op:

- Populariteit: populariteit wordt bepaald door het Download aantal
- A-Z-alfabetisch op pakket naam
- Recent: pakketten worden weer gegeven in de volg orde van publicatie datum

## <a name="search-box"></a>Zoekvak

Met het zoekvak kunnen gebruikers de pakketten zoeken op tref woorden.
Zie [Galerie Zoek syntaxis](search-syntax.md)voor meer informatie.
