---
ms.date: 10/20/2019
keywords: Power shell, cmdlet
title: De Power shell-documentatie gebruiken
ms.openlocfilehash: 50b054ddc21d55946969414688306fc0d15a5adf
ms.sourcegitcommit: d36db3a1bc44aee6bc97422b557041c3aece4c67
ms.translationtype: MT
ms.contentlocale: nl-NL
ms.lasthandoff: 03/21/2020
ms.locfileid: "80082837"
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

![versie kiezer](media/how-to-use-docs/version-search.gif)

U kunt controleren welke versie van Power shell u gebruikt door de `$PSversionTable.PSVersion` waarde te controleren. In het volgende voor beeld ziet u de uitvoer voor Windows Power shell v 5.1.

```powershell
$PSVersionTable.PSVersion
```

```Output
Major  Minor  Build  Revision
-----  -----  -----  --------
5      1      18362  145
```
