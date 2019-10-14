---
ms.date: 09/25/2019
keywords: Power shell, cmdlet
title: De Power shell-documentatie gebruiken
ms.openlocfilehash: 9e3d5828d6bdb4ef14701994f146354a041efaea
ms.sourcegitcommit: a80bb79b85deab8ae3c21de56d1ee432fdd92628
ms.translationtype: MT
ms.contentlocale: nl-NL
ms.lasthandoff: 10/11/2019
ms.locfileid: "72281653"
---
# <a name="how-to-use-the-powershell-documentation"></a>De Power shell-documentatie gebruiken

Welkom bij de online documentatie voor Power shell. Deze site bevat een cmdlet-verwijzing voor de volgende versies van Power shell:

- Power shell 7 (preview-versie)
- Power shell 6
- Power shell 5,1
- Power shell 5,0
- Power Shell 4,0
- Power Shell 3,0

## <a name="selecting-your-version"></a>Uw versie selecteren

Deze site geeft standaard documentatie weer voor de meest recente versie van Power shell. Sommige cmdlets werken anders in verschillende versies van Power shell. Zorg ervoor dat u de documentatie bekijkt voor de versie van Power shell die u gebruikt.

Gebruik de versie kiezer boven aan de pagina om de gewenste versie van Power shell te selecteren.

![versie kiezer](images/how-to-use-docs/picker-vall.gif)

U kunt controleren welke versie van Power shell u gebruikt door de waarde voor de `$PSversionTable.PSVersion` te controleren. In het volgende voor beeld ziet u de uitvoer voor Windows Power shell v 5.1.

```powershell
$PSVersionTable.PSVersion
```

```Output
Major  Minor  Build  Revision
-----  -----  -----  --------
5      1      18362  145
```

## <a name="searching-for-articles"></a>Zoeken naar artikelen

Er zijn twee manieren om te zoeken naar inhoud in docs. De eenvoudigste manier is het vak Filteren onder versie kiezer te gebruiken. U hoeft alleen maar een woord in te voeren dat wordt weer gegeven in de titel van een artikel. Op de pagina wordt een lijst met overeenkomende artikelen weer gegeven. U kunt ook de optie selecteren om te zoeken in de hele site vanuit deze lijst.

![vak filteren](images/how-to-use-docs/filter-search.gif)
