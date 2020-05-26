---
ms.date: 05/22/2020
keywords: powershell,cmdlet
title: De Power shell-documentatie gebruiken
ms.openlocfilehash: 259eb1eea1dc7e8b5ae5730f97c938b838a320bf
ms.sourcegitcommit: 2aec310ad0c0b048400cb56f6fa64c1e554c812a
ms.translationtype: MT
ms.contentlocale: nl-NL
ms.lasthandoff: 05/23/2020
ms.locfileid: "83808262"
---
# <a name="how-to-use-the-powershell-documentation"></a>De Power shell-documentatie gebruiken

Welkom bij de online documentatie voor Power shell. Deze site bevat een cmdlet-verwijzing voor de volgende versies van Power shell:

- Power shell 7
- Power shell 6
- PowerShell 5.1

## <a name="finding-articles-and-selecting-a-version"></a>Artikelen zoeken en een versie selecteren

Er zijn twee manieren om te zoeken naar inhoud in docs. De eenvoudigste manier is het vak Filteren onder versie kiezer te gebruiken. U hoeft alleen maar een woord in te voeren dat wordt weer gegeven in de titel van een artikel. Op de pagina wordt een lijst met overeenkomende artikelen weer gegeven. U kunt ook de optie selecteren om te zoeken in de hele site vanuit deze lijst.

Deze site geeft standaard documentatie weer voor de meest recente versie van Power shell. Sommige cmdlets werken anders in verschillende versies van Power shell. Zorg ervoor dat u de documentatie bekijkt voor de versie van Power shell die u gebruikt.

Gebruik de versie kiezer boven aan de pagina om de gewenste versie van Power shell te selecteren.

![versiekiezer](media/how-to-use-docs/version-search.gif)

U kunt controleren welke versie van Power shell u gebruikt door de waarde te controleren `$PSversionTable.PSVersion` . In het volgende voor beeld ziet u de uitvoer voor Windows Power shell v 5.1.

```powershell
$PSVersionTable.PSVersion
```

```Output
Major  Minor  Build  Revision
-----  -----  -----  --------
5      1      18362  145
```

## <a name="finding-articles-for-previous-versions"></a>Artikelen zoeken voor eerdere versies

Documentatie voor oudere versies van Power shell is gearchiveerd in onze [vorige versies](https://aka.ms/PSLegacyDocs) site.

Deze site bevat documentatie voor de volgende onderwerpen:

- PowerShell 3.0
- PowerShell 4.0
- PowerShell 5.0
- Power shell-werk stromen
- Power shell-webtoegang
