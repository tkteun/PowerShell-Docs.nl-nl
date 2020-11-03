---
description: Hierin wordt beschreven hoe u opdrachten kunt ophalen en uitvoeren in de opdracht geschiedenis.
keywords: powershell,cmdlet
Locale: en-US
ms.date: 05/13/2020
online version: https://docs.microsoft.com/powershell/module/microsoft.powershell.core/about/about_history?view=powershell-7.1&WT.mc_id=ps-gethelp
schema: 2.0.0
title: about_History
ms.openlocfilehash: 8a79690cc409919286d0f14130df72a7fe278010
ms.sourcegitcommit: f874dc1d4236e06a3df195d179f59e0a7d9f8436
ms.translationtype: MT
ms.contentlocale: nl-NL
ms.lasthandoff: 10/13/2020
ms.locfileid: "93252151"
---
# <a name="about-history"></a>Over geschiedenis

## <a name="short-description"></a>Korte beschrijving
Hierin wordt beschreven hoe u opdrachten kunt ophalen en uitvoeren in de opdracht geschiedenis.

## <a name="long-description"></a>Lange beschrijving

Wanneer u een opdracht bij de opdracht prompt invoert, slaat Power shell de opdracht op in de opdracht geschiedenis. U kunt de opdrachten in de geschiedenis gebruiken als een record van uw werk. En u kunt de opdrachten intrekken en uitvoeren vanuit de opdracht geschiedenis.

Power Shell heeft twee verschillende geschiedenis providers: de ingebouwde geschiedenis en de geschiedenis die worden beheerd door de **PSReadLine** -module. De geschiedenis wordt afzonderlijk beheerd, maar beide geschiedenissen zijn beschikbaar in sessies waarin **PSReadLine** wordt geladen.

## <a name="using-the-psreadline-history"></a>De PSReadLine-geschiedenis gebruiken

De PSReadLine-geschiedenis registreert de opdrachten die worden gebruikt in alle Power shell-sessies.
De geschiedenis wordt per host naar een centraal bestand geschreven. Dat geschiedenis bestand is beschikbaar voor alle sessies en bevat alle eerdere geschiedenis. De geschiedenis wordt niet verwijderd wanneer de sessie wordt beëindigd. Deze geschiedenis kan ook niet worden beheerd door de- `*-History` cmdlets. Zie [about_PSReadLine](../../PSReadLine/About/about_PSReadLine.md)voor meer informatie.

## <a name="using-the-built-in-session-history"></a>De ingebouwde sessie geschiedenis gebruiken

Met de ingebouwde geschiedenis worden alleen de opdrachten bijgehouden die in de huidige sessie worden gebruikt. De geschiedenis is niet beschikbaar voor andere sessies en wordt verwijderd wanneer de sessie wordt beëindigd.

### <a name="history-cmdlets"></a>Geschiedenis-cmdlets

Power Shell heeft een set cmdlets die de opdracht Geschiedenis beheren.

| Cmdlet           | Alias  | Beschrijving                                |
| ---------------- | ------ | ------------------------------------------ |
| `Get-History`    | `h`    | Hiermee haalt u de opdracht geschiedenis.                  |
| `Invoke-History` | `r`    | Hiermee voert u een opdracht uit in de opdracht geschiedenis.     |
| `Add-History`    |        | Hiermee voegt u een opdracht toe aan de opdracht geschiedenis.     |
| `Clear-History`  | `clhy` | Hiermee verwijdert u opdrachten uit de opdracht geschiedenis. |

### <a name="keyboard-shortcuts-for-managing-history"></a>Sneltoetsen voor het beheren van de geschiedenis

In de Power shell-console kunt u de volgende snelkoppelingen gebruiken om de opdracht geschiedenis te beheren.

- <kbd>Pijl-omhoog</kbd> : Hiermee wordt de vorige opdracht weer gegeven.
- <kbd>DownArrow</kbd> : de volgende opdracht wordt weer gegeven.
- <kbd>F7</kbd> : Hiermee wordt de opdracht geschiedenis weer gegeven.
- <kbd>ESC</kbd> : om de geschiedenis te verbergen.
- <kbd>F8</kbd> : Hiermee vindt u een opdracht. Typ een of meer tekens en druk vervolgens op <kbd>F8</kbd>. Druk nogmaals op <kbd>F8</kbd> het volgende exemplaar.
- <kbd>F9</kbd> : een opdracht zoeken op geschiedenis-id. Typ de geschiedenis-ID en druk vervolgens op <kbd>F9</kbd>. Druk op <kbd>F7</kbd> om de id te vinden.
- <kbd>#</kbd>`<string>`</kbd><kbd>Tabblad</kbd> : Zoek de geschiedenis voor `*<string>*` en retourneert de meest recente overeenkomst. Als u herhaaldelijk op <kbd>Tab</kbd> drukt, worden de overeenkomende items in uw geschiedenis door lopen.

> [!NOTE]
> Deze sleutel bindingen worden geïmplementeerd door de host-toepassing van de console. Andere toepassingen, zoals Visual Studio code of Windows Terminal, kunnen verschillende sleutel bindingen hebben. De bindingen kunnen worden overschreven door de PSReadLine-module. PSReadLine wordt automatisch geladen wanneer u een Power shell-sessie start.
> Als PSReadLine is geladen, zijn <kbd>F7</kbd> en <kbd>F9</kbd> niet gebonden aan een functie. PSReadLine biedt geen vergelijk bare functionaliteit. Zie [about_PSReadLine](../../PSReadLine/About/about_PSReadLine.md)voor meer informatie.

### <a name="maximumhistorycount"></a>MaximumHistoryCount

De `$MaximumHistoryCount` Voorkeurs variabele bepaalt het maximum aantal opdrachten dat door Power shell wordt opgeslagen in de opdracht geschiedenis. De standaardwaarde is 
4096.

Met de volgende opdracht wordt bijvoorbeeld de 100- `$MaximumHistoryCount` opdrachten verkort:

```powershell
$MaximumHistoryCount = 100
```

Als u de instelling wilt Toep assen, start u Power shell opnieuw.

Als u de nieuwe waarde voor de variabele wilt opslaan voor alle Power shell-sessies, voegt u de toewijzings instructie toe aan een Power shell-profiel. Zie [about_Profiles](about_Profiles.md)voor meer informatie over profielen.

Zie about_Preference_Variables voor meer informatie over de `$MaximumHistoryCount` Voorkeurs variabele [about_Preference_Variables](about_Preference_Variables.md).

### <a name="order-of-commands-in-the-history"></a>Volg orde van opdrachten in de geschiedenis

Opdrachten worden toegevoegd aan de geschiedenis wanneer de opdracht wordt uitgevoerd, niet wanneer de opdracht wordt ingevoerd. Als opdrachten enige tijd in beslag nemen of als de opdrachten worden uitgevoerd in een geneste prompt, worden de opdrachten mogelijk niet in de juiste volg orde weer gegeven in de geschiedenis. Opdrachten die in een geneste prompt worden uitgevoerd, worden alleen uitgevoerd wanneer u het prompt niveau verlaat.

## <a name="see-also"></a>Zie ook

- [about_Line_Editing](about_Line_Editing.md)
- [about_Preference_Variables](about_Preference_Variables.md)
- [about_Profiles](about_Profiles.md)
- [about_Variables](about_Variables.md)
- [about_PSReadLine](../../PSReadLine/About/about_PSReadLine.md)

