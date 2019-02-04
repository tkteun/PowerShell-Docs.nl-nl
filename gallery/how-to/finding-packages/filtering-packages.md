---
ms.date: 06/12/2017
contributor: JKeithB
keywords: Galerie, powershell, cmdlet, psgallery
title: Zoekresultaten filteren
ms.openlocfilehash: 13270a310613a974e1588a9f56d443a936cfebb8
ms.sourcegitcommit: b6871f21bd666f9cd71dd336bb3f844cf472b56c
ms.translationtype: MT
ms.contentlocale: nl-NL
ms.lasthandoff: 02/03/2019
ms.locfileid: "55687592"
---
# <a name="filtering-search-results"></a>Zoekresultaten filteren

De [pakketten tabblad](https://www.powershellgallery.com/packages) weergegeven van alle beschikbare pakketten in de PowerShell Gallery.

Er zijn verschillende manieren om te filteren, sorteren en zoeken van de pakketten.
Voor meer informatie over een bepaald pakket, klikt u op het pakket.

## <a name="filter-by"></a>Filteren op

De vervolgkeuzelijst onder 'Filteren op' kan gebruikers om de resultaten door te filteren:
- Voorlopige versie opnemen
- Alleen stabiel

Zie voor meer informatie over 'Voorlopige versie' en "Stabiele" [voorlopige versie versiebeheer toegevoegd aan PowerShellGet en PowerShell Gallery](https://blogs.msdn.microsoft.com/powershell/2017/12/05/prerelease-versioning-added-to-powershellget-and-powershell-gallery/) in de Blog van het PowerShell-Team.

De selectievakjes onder de vervolgkeuzelijst toestaan dat gebruikers om de resultaten door te filteren:
- Pakkettypen
  - Module
  - Script
- Categorieën
  - Cmdlet
  - DSC Resource
  - Functie
  - Mogelijkheid van de rol
  - Werkstroom

Als u wilt zien alleen modules in de PowerShell Gallery, Module in de pakkettypen controleren
Controleer op dezelfde manier als u wilt zien alleen scripts die in de PowerShell Gallery, Script in de pakkettypen.

> [!NOTE]
> Filters zijn inclusief.
> Voorbeeld: Een pakket op met zowel cmdlets en -functies wordt weergegeven als een Cmdlet of functie (of beide) worden gecontroleerd.
> Als geen van beide zijn geselecteerd, wordt het pakket niet weergegeven.
> Alle categorieën zijn geselecteerd, wordt alleen de pakketten met een van deze categorieën worden weergegeven.
> **Pakketten die niet tot een van deze categorieën behoren worden niet weergegeven.**

## <a name="sort-by"></a>Sorteren op

De sorteren op vervolgkeuzelijst kan gebruikers de resultaten sorteren op:
- Populariteit - populariteit wordt bepaald door het aantal downloaden
- A-Z - alfabetisch op pakketnaam
- Recente - pakketten worden weergegeven in de volgorde van publiceren-datum

## <a name="search-box"></a>Zoekvak

Het zoekvak kunnen gebruikers de pakketten op trefwoorden zoeken.
Zie voor meer informatie, [galerie Zoeksyntaxis](search-syntax.md).
