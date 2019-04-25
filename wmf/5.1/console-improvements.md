---
ms.date: 06/12/2017
keywords: wmf,powershell,installeren
title: Verbeteringen in de console in WMF 5.1
ms.openlocfilehash: a8e82e2f973916c2ed5007eba90ee6f2b7a9a769
ms.sourcegitcommit: e7445ba8203da304286c591ff513900ad1c244a4
ms.translationtype: MT
ms.contentlocale: nl-NL
ms.lasthandoff: 04/23/2019
ms.locfileid: "62085123"
---
# <a name="console-improvements-in-wmf-51"></a>Verbeteringen in de console in WMF 5.1

## <a name="powershell-console-improvements"></a>Verbeteringen in de console van PowerShell

De volgende wijzigingen zijn aangebracht naar powershell.exe in WMF 5.1 om de console-ervaring te verbeteren:

### <a name="vt100-support"></a>Ondersteuning voor VT100

Windows 10 is ondersteuning toegevoegd voor [VT100 escapereeksen](/windows/console/console-virtual-terminal-sequences).
PowerShell worden bepaalde VT100 opmaak escapereeksen genegeerd bij het berekenen van de tabelbreedte van de.

PowerShell toegevoegd ook een nieuwe API die kan worden gebruikt in de opmaak van code om te bepalen of VT100 wordt ondersteund.
Bijvoorbeeld:

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

Dit is een complete [voorbeeld](https://gist.github.com/lzybkr/dcb973dccd54900b67783c48083c28f7) kunnen worden gebruikt voor het markeren van treffers van `Select-String`.
Opslaan van het voorbeeld in een bestand met de naam `MatchInfo.format.ps1xml`, voert u als u wilt gebruiken, in uw profiel of ergens anders, `Update-FormatData -Prepend MatchInfo.format.ps1xml`.

Houd er rekening mee dat VT100 escapereeksen worden alleen ondersteund vanaf de Windows 10 Verjaardag update; ze worden niet ondersteund op oudere systemen.

### <a name="vi-mode-support-in-psreadline"></a>Ondersteuning voor VI-modus in PSReadline

[PSReadline](https://github.com/lzybkr/PSReadLine) voegt ondersteuning toe voor vi-modus. Voor het gebruik van vi modus uitvoeren `Set-PSReadlineOption -EditMode Vi`.

### <a name="redirected-stdin-with-interactive-input"></a>Omgeleide stdin met interactieve invoer

In eerdere versies, PowerShell met starten `powershell -File -` is vereist wanneer stdin is omgeleid en u wilt opdrachten interactief invoeren.

Met WMF 5.1, dit moeilijk te detecteren optie is niet meer nodig.
U kunt PowerShell starten zonder opties, bijvoorbeeld `powershell`.

Houd er rekening mee dat PSReadline biedt momenteel geen ondersteuning voor omgeleid stdin, en de ingebouwde opdrachtregel bewerken ervaring met omgeleide stdin is zeer beperkte, bijvoorbeeld pijltoetsen werken niet.
Een toekomstige release van PSReadline moet dit probleem oplossen.