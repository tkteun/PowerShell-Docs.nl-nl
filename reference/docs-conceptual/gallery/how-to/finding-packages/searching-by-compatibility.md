---
ms.date: 12/11/2018
contributor: JKeithB, SydneyhSmith
keywords: Galerie, Power shell, cmdlet, psgallery
title: Pakketten met compatibele Power shell-edities of besturings systeem
ms.openlocfilehash: b414ce2c2b189e9da150cbe612e0bb2572d39e76
ms.sourcegitcommit: 6545c60578f7745be015111052fd7769f8289296
ms.translationtype: MT
ms.contentlocale: nl-NL
ms.lasthandoff: 04/22/2020
ms.locfileid: "78278351"
---
# <a name="packages-with-compatible-powershell-editions-or-operating-systems"></a>Pakketten met compatibele Power shell-edities of-besturings systemen

Vanaf versie 5,1 is Power shell beschikbaar in verschillende edities waarin verschillende functie sets en platform compatibiliteit worden aangegeven.

## <a name="searching-by-powershell-edition"></a>Zoeken op Power shell-editie

De twee versies van Power shell zijn:
- **Desktop-editie:** deze editie is gebaseerd op .NET Framework en biedt compatibiliteit met scripts en modules die zijn gericht op versies van PowerShell die worden uitgevoerd op edities van Windows met een volledige footprint zoals Server Core en Windows Desktop.
- **Core-editie:** deze editie is gebaseerd op .NET Framework en biedt compatibiliteit met scripts en modules die zijn gericht op versies van PowerShell die worden uitgevoerd op edities van Windows met een verminderde footprint zoals Nano Server en Windows IoT.

### <a name="powershell-gallery-allows-you-to-filter-packages-compatible-for-specific-powershell-editions"></a>Met PowerShell Gallery kunt u pakketten filteren die compatibel zijn voor specifieke Power shell-edities

Als voor een pakket compatibele PSEditions is opgegeven, worden deze vermeld als onderdeel van Power shell-edities op de pagina pakket weergave en ook in pakketten met resultaten.
U kunt ook zoeken naar compatibele pakketten met behulp van Power shell.

![Pagina item weergave met PSEditions](media/searching-by-compatibility/packagedisplaypagewithpseditions.PNG)

### <a name="search-for-packages-in-the-gallery-ui-that-work-on-powershell-core"></a>Pakketten zoeken in de gebruikers interface van de galerie die werkt met Power shell core

Tags: "PSEdition_Desktop" en Tags: "PSEdition_Core" gebruiken om de pakketten op PowerShell Gallery te filteren.

### <a name="use-tagspsedition_core-to-search-items-compatible-with-powershell-core-edition"></a>Tags gebruiken: ' PSEdition_Core ' om items te zoeken die compatibel zijn met Power shell Core Edition.

![Zoek resultaten voor items die compatibel zijn met Core PSEdition](media/searching-by-compatibility/searchresultswithpseditions.PNG)

### <a name="use-tagspsedition_desktop-to-search-items-compatible-with-powershell-desktop-edition"></a>Tags gebruiken: ' PSEdition_Desktop ' om items te zoeken die compatibel zijn met Power shell Desktop Edition.

![Zoek resultaten voor items die compatibel zijn met Desktop PSEdition](media/searching-by-compatibility/searchresultswithpseditionsdesktop.PNG)

### <a name="search-for-packages-to-find-compatible-editions-using-powershell"></a>Pakketten zoeken om compatibele versies te vinden met behulp van Power shell
U kunt labels opgeven voor het filteren van de Power shell-editie en het besturings systeem.
U gebruikt de `Find-Package` cmdlet waarmee de `-Tag` para meter wordt opgegeven voor de editie (en het besturings systeem) waarop u zich wilt richten.
Zo:

```powershell
# Find modules compatible with PowerShell Core:
Find-Module -Tag PSEdition_Core

# Find modules compatible with PowerShell Core on Linux:
Find-Module -Tag PSEdition_Core, Linux
```

## <a name="searching-by-operating-system"></a>Zoeken op besturings systeem

Omdat Power shell core beschikbaar is voor Windows, Linux en MacOS, kunnen pakketten in de galerie worden ontworpen voor een combi natie van deze besturings systemen. Gebruik in de gebruikers interface van de galerie de volgende zoek tags om pakketten te vinden die zijn gelabeld door het besturings systeem:

- Tags: "Windows"
- Tags: Linux
- Tags: "MacOS"

U kunt deze tags op `Find-Module` (en andere cmdlets in de PowerShellGet-module) als volgt opgeven:

```powershell
# Find Modules compatible with Windows
Find-Module -Tag Linux
```

## <a name="searching-for-multiple-compatibilities"></a>Zoeken naar meerdere compatibiliteits problemen

U kunt zoeken naar een pakket met meerdere compatibiliteit met behulp van de syntaxis:

Tags: "Compatibility1" "Compatibility2"

Als u bijvoorbeeld zoekt naar een pakket met Power shell core-compatibiliteit dat op zowel mijn Windows-als Linux-computers wordt uitgevoerd, gebruikt u de zoek Tags:

Tags: "PSEdition_Core" "Windows" "Linux"

Als u wilt zoeken met behulp van Power `Find-Module` shell, kunt u de (en de andere cmdlets in de PowerShellGet-module) gebruiken, bijvoorbeeld:

```powershell
# Find scripts compatible with PowerShell Core, Windows, and Linux
Find-Script -Tag PSEdition_Core,Linux,Windows

# Find modules compatible with PowerSHellCore and MacOS
Find-Module -Tag PSEdition_Core,MacOS
```

## <a name="more-details-on-authoring-and-finding-the-packages-with-compatible-powershell-editions"></a>Meer informatie over het ontwerpen en vinden van de pakketten met compatibele Power shell-edities

- [Modules met PSEditions](../../concepts/module-psedition-support.md)
- [Scripts met PSEditions](../../concepts/script-psedition-support.md)
