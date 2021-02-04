---
ms.date: 07/29/2020
keywords: powershell,cmdlet
ms.topic: how-to
title: De Power shell-documentatie gebruiken
description: In deze artikelen wordt uitgelegd hoe u de functies van deze site gebruikt, inclusief het filteren van zoeken en de versie selectie.
ms.openlocfilehash: 4779e6e4b17c461d71e9d613d1184b9ce2e7ab7b
ms.sourcegitcommit: df5e6f032ee2d4b556d50406832732d2f7dc2502
ms.translationtype: MT
ms.contentlocale: nl-NL
ms.lasthandoff: 01/14/2021
ms.locfileid: "98216079"
---
# <a name="how-to-use-the-powershell-documentation"></a>De Power shell-documentatie gebruiken

Welkom bij de online documentatie voor Power shell. Deze site bevat een cmdlet-verwijzing voor de volgende versies van Power shell:

- Power shell 7,2 (Prerelease)
- Power shell 7,1 (actueel)
- Power shell 7,0 (LTS)
- PowerShell 5.1

## <a name="finding-articles-and-selecting-a-version"></a>Artikelen zoeken en een versie selecteren

Er zijn twee manieren om te zoeken naar inhoud in docs. De eenvoudigste manier is het vak Filteren onder versie kiezer te gebruiken. U hoeft alleen maar een woord in te voeren dat wordt weer gegeven in de titel van een artikel. Op de pagina wordt een lijst met overeenkomende artikelen weer gegeven. U kunt ook de optie selecteren om te zoeken in de hele site vanuit deze lijst.

Deze site geeft standaard documentatie weer voor de meest recente versie van Power shell. Sommige cmdlets werken anders in verschillende versies van Power shell. Zorg ervoor dat u de documentatie bekijkt voor de versie van Power shell die u gebruikt.

Gebruik de versie kiezer boven aan de pagina om de gewenste versie van Power shell te selecteren.

![De versie kiezer gebruiken](media/how-to-use-docs/version-search.gif)

U kunt controleren welke versie van Power shell u gebruikt door de waarde te controleren `$PSversionTable.PSVersion` . In het volgende voor beeld ziet u de uitvoer voor Windows Power shell 5,1.

```powershell
$PSVersionTable.PSVersion
```

```Output
Major  Minor  Build  Revision
-----  -----  -----  --------
5      1      19041  1
```

Zie [about_Command_Syntax](/powershell/module/microsoft.powershell.core/about/about_command_syntax)als u geen ervaring hebt met Power shell en meer informatie wilt over de syntaxis van de opdracht.

## <a name="finding-articles-for-previous-versions"></a>Artikelen zoeken voor eerdere versies

Documentatie voor oudere versies van Power shell is gearchiveerd in onze [vorige versies](https://aka.ms/PSLegacyDocs) site.

Deze site bevat documentatie voor de volgende onderwerpen:

- PowerShell 3.0
- PowerShell 4.0
- PowerShell 5.0
- Power shell 6
- Power shell-werk stromen
- Power shell-webtoegang
