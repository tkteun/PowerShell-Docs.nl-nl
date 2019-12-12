---
ms.date: 06/12/2017
keywords: wmf,powershell,installeren
title: Verbeteringen van de console in WMF 5.1
ms.openlocfilehash: d0dd8e3c31dc0ddebab1bb899468b77a9292954d
ms.sourcegitcommit: debd2b38fb8070a7357bf1a4bf9cc736f3702f31
ms.translationtype: MT
ms.contentlocale: nl-NL
ms.lasthandoff: 12/05/2019
ms.locfileid: "71145052"
---
# <a name="console-improvements-in-wmf-51"></a>Verbeteringen van de console in WMF 5.1

## <a name="powershell-console-improvements"></a>Verbeteringen in de Power shell-console

De volgende wijzigingen zijn aangebracht in Power shell. exe in WMF 5,1 om de console-ervaring te verbeteren:

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

Hier volgt een volledig [voor beeld](https://gist.github.com/lzybkr/dcb973dccd54900b67783c48083c28f7) dat kan worden gebruikt om overeenkomsten van `Select-String`te markeren. Sla het voor beeld op in een bestand met de naam `MatchInfo.format.ps1xml`en gebruik het vervolgens in uw profiel of ergens anders en voer `Update-FormatData -Prepend MatchInfo.format.ps1xml`uit.

Houd er rekening mee dat VT100-escape reeksen alleen worden ondersteund vanaf de Windows 10 jubileum update.
Ze worden niet ondersteund op eerdere systemen.

### <a name="vi-mode-support-in-psreadline"></a>Ondersteuning voor de VI-modus in PSReadline

[PSReadline](https://github.com/PowerShell/PSReadLine) voegt ondersteuning toe voor de modus voor VI. Als u de modus VI wilt gebruiken, voert u `Set-PSReadlineOption -EditMode Vi`uit.

### <a name="redirected-stdin-with-interactive-input"></a>Omgeleide stdin met interactieve invoer

In eerdere versies was het starten van Power shell met `powershell -File -` vereist toen stdin werd omgeleid en wilt u opdrachten interactief invoeren.

Met WMF 5,1 is deze optie moeilijk te detecteren niet meer nodig. U kunt Power shell zonder opties starten.

Houd er rekening mee dat PSReadline geen ondersteuning biedt voor omgeleide stdin en dat de ingebouwde opdracht regel functie voor het bewerken van een omgeleide stdin een zeer beperkt aantal, bijvoorbeeld pijl toetsen niet werkt. Een toekomstige release van PSReadline moet dit probleem oplossen.