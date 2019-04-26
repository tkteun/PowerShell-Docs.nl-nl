---
ms.date: 12/11/2018
contributor: JKeithB, SydneyhSmith
keywords: Galerie, powershell, cmdlet, psgallery
title: Pakketten met compatibel besturingssysteem of PowerShell-edities
ms.openlocfilehash: 14038aa9b0453e1d06e6587e97da391b56297c75
ms.sourcegitcommit: e7445ba8203da304286c591ff513900ad1c244a4
ms.translationtype: MT
ms.contentlocale: nl-NL
ms.lasthandoff: 04/23/2019
ms.locfileid: "62084560"
---
# <a name="packages-with-compatible-powershell-editions-or-operating-systems"></a>Pakketten met compatibele PowerShell-edities en besturingssystemen

Vanaf versie 5.1 is is PowerShell beschikbaar in verschillende edities die staan voor verschillende functies en platform compatibiliteiten.

## <a name="searching-by-powershell-edition"></a>Te zoeken via PowerShell-editie

De twee edities van PowerShell zijn:
- **Desktop-editie:** Gebaseerd op .NET Framework en biedt compatibiliteit met scripts en modules die zijn gericht op versies van PowerShell die worden uitgevoerd op edities van Windows, zoals Server Core- en Windows Desktop volledige footprint.
- **Core-editie:** Gebaseerd op .NET Core en biedt compatibiliteit met scripts en modules die zijn gericht op versies van PowerShell die worden uitgevoerd op edities van Windows, zoals Nano Server en Windows IoT verminderde footprint.

### <a name="powershell-gallery-allows-you-to-filter-packages-compatible-for-specific-powershell-editions"></a>PowerShell Gallery kunt u voor het filteren van pakketten die compatibel is voor bepaalde PowerShell-edities

Als een pakket met compatibele PSEditions opgegeven, ze worden weergegeven als onderdeel van de PowerShell-edities op de pagina van het pakket weergeven en in de pakketten resultaten.
U kunt ook zoeken naar compatibele pakketten met behulp van PowerShell.

![Pagina voor item weergeven met PSEditions](../../Images/packagedisplaypagewithpseditions.PNG)

### <a name="search-for-packages-in-the-gallery-ui-that-work-on-powershell-core"></a>Zoeken naar pakketten in de UI-galerie die in PowerShell Core werken

Codes gebruiken: Tags en "PSEdition_Desktop": "PSEdition_Core" met filters in de pakketten op PowerShell Gallery.

### <a name="use-tagspseditioncore-to-search-items-compatible-with-powershell-core-edition"></a>Codes gebruiken: "PSEdition_Core" om te zoeken naar items die compatibel is met PowerShell Core-editie.

![Zoekresultaten voor items die compatibel is met Core PSEdition](../../Images/searchresultswithpseditions.PNG)

### <a name="use-tagspseditiondesktop-to-search-items-compatible-with-powershell-desktop-edition"></a>Codes gebruiken: "PSEdition_Desktop" om te zoeken naar items die compatibel is met de PowerShell-Desktop-editie.

![Zoekresultaten voor items die compatibel is met Desktop PSEdition](../../Images/searchresultswithpseditionsdesktop.PNG)

### <a name="search-for-packages-to-find-compatible-editions-using-powershell"></a>Zoeken naar pakketten te vinden compatibel is met behulp van PowerShell-edities
U kunt tags te filteren voor de PowerShell-editie en het besturingssysteem opgeven.
U gebruikt de `Find-Package` cmdlet op te geven de `-Tag` parameter opgeven voor de editie (en besturingssysteem) u ontwikkelt.
Als volgt:

```powershell
# Find modules compatible with PowerShell Core:
Find-Module -Tag PSEdition_Core

# Find modules compatible with PowerShell Core on Linux:
Find-Module -Tag PSEdition_Core, Linux
```

## <a name="searching-by-operating-system"></a>Zoeken op besturingssysteem

Omdat PowerShell Core beschikbaar voor Windows, Linux en Mac OS is, kunnen de pakketten in de galerie zijn ontworpen voor elke combinatie van deze besturingssystemen. In de gebruikersinterface van de galerie door de volgende searchs-codes te vinden van pakketten die zijn gemarkeerd door het besturingssysteem te gebruiken:

- Tags: "Windows"
- Tags: "Linux"
- Tags: "MacOS"

U kunt deze tags opgeven op `Find-Module` (en andere cmdlets in de PowerShellGet-module), zoals deze:

```powershell
# Find Modules compatible with Windows
Find-Module -Tag Linux
```

## <a name="searching-for-multiple-compatibilities"></a>Zoeken naar meerdere compatibiliteiten

U kunt zoeken naar een pakket met meerdere compatibiliteiten met behulp van de syntaxis:

Tags: "Compatibility1" "Compatibility2"

Als u een pakket met de compatibiliteit van de PowerShell Core die wordt uitgevoerd op mijn Windows- en Linux-machines zoekt, bijvoorbeeld de search-codes gebruiken:

Tags: "PSEdition_Core" "Windows" "Linux"

Als u wilt zoeken met behulp van PowerShell, kunt u de `Find-Module` (en de andere cmdlets in de PowerShellGet-module), zoals deze:

```powershell
# Find scripts compatible with PowerShell Core, Windows, and Linux
Find-Script -Tag PSEdition_Core,Linux,Windows

# Find modules compatible with PowerSHellCore and MacOS
Find-Module -Tag PSEdition_Core,MacOS
```

## <a name="more-details-on-authoring-and-finding-the-packages-with-compatible-powershell-editions"></a>Meer informatie over het ontwerpen en zoeken van de pakketten met compatibele PowerShell-edities

- [Modules met PSEditions](../../concepts/module-psedition-support.md)
- [Scripts met PSEditions](../../concepts/script-psedition-support.md)
