---
ms.date: 06/12/2017
keywords: wmf,powershell,installeren
title: Verbeteringen in de beheerconsole in WMF 5.1
ms.openlocfilehash: fb689002caf42203d760f11acc64e52cfa681069
ms.sourcegitcommit: 54534635eedacf531d8d6344019dc16a50b8b441
ms.translationtype: MT
ms.contentlocale: nl-NL
ms.lasthandoff: 05/16/2018
ms.locfileid: "34189309"
---
# <a name="console-improvements-in-wmf-51"></a>Verbeteringen in de beheerconsole in WMF 5.1#

## <a name="powershell-console-improvements"></a>Verbeteringen in de beheerconsole PowerShell

De volgende wijzigingen zijn aangebracht aan powershell.exe in WMF 5.1 om de console-ervaring te verbeteren:

###<a name="vt100-support"></a>VT100-ondersteuning

Windows 10 is ondersteuning toegevoegd voor [VT100 escapereeksen](https://msdn.microsoft.com/en-us/library/windows/desktop/mt638032(v=vs.85).aspx).
PowerShell worden bepaalde VT100 opmaak escapereeksen genegeerd bij het berekenen van de Tabelbreedten.

PowerShell toegevoegd ook een nieuwe API die kan worden gebruikt in de opmaak opgeven om te bepalen of VT100 wordt ondersteund.
Bijvoorbeeld:

```
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
Hier volgt een volledige [voorbeeld](https://gist.github.com/lzybkr/dcb973dccd54900b67783c48083c28f7) die kunnen worden gebruikt om te markeren overeenkomsten uit de Select-tekenreeks.
Opslaan van het voorbeeld in een bestand met de naam `MatchInfo.format.ps1xml`, voert u voor het gebruik ervan in uw profiel of elders, `Update-FormatData -Prepend MatchInfo.format.ps1xml`.

Houd er rekening mee dat VT100 escapereeksen worden alleen ondersteund met de update voor Windows 10 Verjaardag; starten ze worden niet ondersteund op oudere systemen.

### <a name="vi-mode-support-in-psreadline"></a>Ondersteuning voor VI-modus in PSReadline

[PSReadline](https://github.com/lzybkr/PSReadLine) voegt ondersteuning toe voor vi-modus. Voer om vi modus gebruiken `Set-PSReadlineOption -EditMode Vi`.

### <a name="redirected-stdin-with-interactive-input"></a>Omgeleide stdin met interactieve invoer

In eerdere versies, PowerShell met vanaf `powershell -File -` is vereist wanneer stdin is omgeleid en u wilt voert opdrachten interactief.

Met WMF 5.1, dit moeilijk te detecteren optie is niet meer nodig.
U kunt PowerShell starten zonder opties, zoals `powershell`.

Let op: PSReadline biedt momenteel geen ondersteuning voor omgeleid stdin, en de ingebouwde opdrachtregel bewerken ervaring met omgeleide stdin is zeer beperkt, bijvoorbeeld pijltoetsen werken niet.
Een toekomstige release van PSReadline moet dit probleem kunt oplossen.
