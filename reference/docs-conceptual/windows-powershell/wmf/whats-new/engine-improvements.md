---
ms.date: 06/12/2017
ms.topic: conceptual
keywords: wmf,powershell,installeren
title: Verbeteringen van PowerShell-engine in WMF 5.1
ms.openlocfilehash: cccfcf8872ac60e0902669bcc797d0ed250317ba
ms.sourcegitcommit: 2aec310ad0c0b048400cb56f6fa64c1e554c812a
ms.translationtype: MT
ms.contentlocale: nl-NL
ms.lasthandoff: 05/23/2020
ms.locfileid: "83810377"
---
# <a name="powershell-engine-improvements"></a>Verbeteringen in Power shell-engine

De volgende verbeteringen voor de kern-Power shell-Engine zijn geïmplementeerd in WMF 5,1:

## <a name="performance"></a>Prestaties

Prestaties zijn verbeterd op enkele belang rijke gebieden:

- Opstarten
- Pipelinen naar cmdlets zoals `ForEach-Object` en `Where-Object` is ongeveer 50% sneller

Enkele voor beelden van verbeteringen (uw resultaten kunnen variëren, afhankelijk van uw hardware):

| Scenario | 5,0 tijd (MS) | 5,1 tijd (MS) |
| -------- | :---------------: | :---------------: |
| `powershell -command "echo 1"` | 900 | 250 |
| Eerste keer dat Power shell wordt uitgevoerd:`powershell -command "Unknown-Command"` | 30.000 | 13000 |
| Ingebouwde opdracht analyse cache:`powershell -command "Unknown-Command"` | 7000 | 520 |
| <code>1..1000000 &#124; % { }</code> | 1400 | 750 |

> [!NOTE]
> Een wijziging met betrekking tot het opstarten kan van invloed zijn op bepaalde niet-ondersteunde scenario's. De bestanden worden niet langer door Power shell gelezen `$pshome\*.ps1xml` : deze bestanden zijn naar C# geconverteerd om te voor komen dat een bestand en CPU-overhead voor het verwerken van de XML-bestanden. De bestanden bestaan nog steeds voor de ondersteuning van v2 naast elkaar, dus als u de bestands inhoud wijzigt, heeft dit geen effect op V5, alleen v2. Houd er rekening mee dat het wijzigen van de inhoud van deze bestanden nooit een ondersteund scenario was.

Een andere zicht bare wijziging is hoe Power shell de geëxporteerde opdrachten en andere informatie voor modules die op een systeem zijn geïnstalleerd, in de cache opslaat. Voorheen werd deze cache opgeslagen in de map `$env:LOCALAPPDATA\Microsoft\Windows\PowerShell\CommandAnalysis` . In WMF 5,1 is de cache één bestand `$env:LOCALAPPDATA\Microsoft\Windows\PowerShell\ModuleAnalysisCache` . Zie [module analyse cache](release-notes.md#module-analysis-cache) voor meer informatie.
