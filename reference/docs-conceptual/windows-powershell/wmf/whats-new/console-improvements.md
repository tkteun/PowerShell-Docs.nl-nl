---
ms.date: 06/12/2017
title: Verbeteringen van de console in WMF 5.1
description: WMF 5,1 voegt nieuwe functies toe aan de console-ervaring voor Windows Power shell 5,1.
ms.openlocfilehash: 9a86a2ed4787554e7255bedf1c2ae6e798fefa45
ms.sourcegitcommit: 488a940c7c828820b36a6ba56c119f64614afc29
ms.translationtype: MT
ms.contentlocale: nl-NL
ms.lasthandoff: 10/27/2020
ms.locfileid: "92660759"
---
# <a name="console-improvements-in-wmf-51"></a>Verbeteringen van de console in WMF 5.1

## <a name="powershell-console-improvements"></a>Verbeteringen in de Power shell-console

De volgende wijzigingen zijn aangebracht in powershell.exe in WMF 5,1 om de console-ervaring te verbeteren:

### <a name="vt100-support"></a>VT100-ondersteuning

Windows 10 heeft ondersteuning toegevoegd voor [VT100-escape reeksen](/windows/console/console-virtual-terminal-sequences).
In Power shell worden bepaalde escape reeksen voor VT100-opmaak genegeerd bij het berekenen van tabel breedten.

Power Shell heeft ook een nieuwe API toegevoegd die in opmaak code kan worden gebruikt om te bepalen of VT100 wordt ondersteund. Bijvoorbeeld:

```powershell
if ($host.UI.SupportsVirtualTerminal)
{
    $esc = [char]0x1b
    "A yellow ${esc}[93mhello${esc}[0m"
}
else
{
    "A default hello"
}
```

Hier volgt een volledig [voor beeld](https://gist.github.com/lzybkr/dcb973dccd54900b67783c48083c28f7) dat kan worden gebruikt voor het markeren van overeenkomsten `Select-String` . Sla het voor beeld op in een bestand met `MatchInfo.format.ps1xml` de naam en voer het vervolgens uit in uw profiel of elders `Update-FormatData -Prepend MatchInfo.format.ps1xml` .

Houd er rekening mee dat VT100-escape reeksen alleen worden ondersteund vanaf de Windows 10 jubileum update.
Ze worden niet ondersteund op eerdere systemen.

### <a name="vi-mode-support-in-psreadline"></a>Ondersteuning voor de VI-modus in PSReadline

[PSReadline](https://github.com/PowerShell/PSReadLine) voegt ondersteuning toe voor de modus voor VI. Als u de modus VI wilt gebruiken, voert u uit `Set-PSReadlineOption -EditMode Vi` .

### <a name="redirected-stdin-with-interactive-input"></a>Omgeleide stdin met interactieve invoer

In eerdere versies was het starten van Power shell met `powershell -File -` was vereist toen stdin werd omgeleid en wilt u opdrachten interactief invoeren.

Met WMF 5,1 is deze optie moeilijk te detecteren niet meer nodig. U kunt Power shell zonder opties starten.

Houd er rekening mee dat PSReadline geen ondersteuning biedt voor omgeleide stdin en dat de ingebouwde opdracht regel functie voor het bewerken van een omgeleide stdin een zeer beperkt aantal, bijvoorbeeld pijl toetsen niet werkt. Een toekomstige release van PSReadline moet dit probleem oplossen.
