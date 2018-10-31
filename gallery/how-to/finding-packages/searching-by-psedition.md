---
ms.date: 06/12/2017
contributor: JKeithB
keywords: Galerie, powershell, cmdlet, psgallery
title: Pakketten met compatibele PowerShell-edities
ms.openlocfilehash: e16cfb0ee30e344c9399bec2985baafc5a252fd7
ms.sourcegitcommit: 98b7cfd8ad5718efa8e320526ca76c3cc4141d78
ms.translationtype: MT
ms.contentlocale: nl-NL
ms.lasthandoff: 10/25/2018
ms.locfileid: "50004042"
---
# <a name="packages-with-compatible-powershell-editions"></a>Pakketten met compatibele PowerShell-edities

Vanaf versie 5.1 is PowerShell beschikbaar in verschillende edities die staan voor verschillende functies en platformcompatibiliteit.

- **Desktop-editie:** deze editie is gebaseerd op .NET Framework en biedt compatibiliteit met scripts en modules die zijn gericht op versies van PowerShell die worden uitgevoerd op edities van Windows met een volledige footprint zoals Server Core en Windows Desktop.
- **Core-editie:** deze editie is gebaseerd op .NET Framework en biedt compatibiliteit met scripts en modules die zijn gericht op versies van PowerShell die worden uitgevoerd op edities van Windows met een verminderde footprint zoals Nano Server en Windows IoT.

## <a name="powershell-gallery-extracts-supported-pseditions-metadata-and-allows-you-to-filters-the-packages-compatible-for-specific-powershell-editions"></a>PowerShell Gallery ondersteunde PSEditions metagegevens worden uitgepakt en kunt u filters de pakketten compatibel voor bepaalde PowerShell-edities

Als een pakket met compatibele PSEditions opgegeven, worden deze weergegeven als onderdeel van de PowerShell-edities op de pagina van het pakket weergeven en in de pakketten resultaten.

![Pagina voor item weergeven met PSEditions](../../Images/manual_package_download.png)

## <a name="search-for-packages-in-the-gallery-ui-which-works-on-powershellcore"></a>Zoeken naar pakketten in de galerie gebruikersinterface die op PowerShellCore werkt

Codes gebruiken: Tags en "PSEdition_Desktop": "PSEdition_Core" met filters in de pakketten op PowerShell Gallery.

### <a name="use-tagspseditioncore-to-search-items-compatible-with-powershell-core-edition"></a>Codes gebruiken: "PSEdition_Core" om te zoeken naar items die compatibel is met PowerShell Core-editie.

![Zoekresultaten voor items die compatibel is met Core PSEdition](../../Images/SearchResultsWithPSEditions.PNG)

### <a name="use-tagspseditiondesktop-to-search-items-compatible-with-powershell-desktop-edition"></a>Codes gebruiken: "PSEdition_Desktop" om te zoeken naar items die compatibel is met de PowerShell-Desktop-editie.

![Zoekresultaten voor items die compatibel is met Desktop PSEdition](../../Images/SearchResultsWithPSEdition-Desktop.PNG)

## <a name="more-details-on-authoring-and-finding-the-packages-with-compatible-powershell-editions"></a>Meer informatie over het ontwerpen en zoeken van de pakketten met compatibele PowerShell-edities

- [Modules met PSEditions](../../concepts/module-psedition-support.md)
- [Scripts met PSEditions](../../concepts/script-psedition-support.md)
