---
ms.date: 06/12/2017
ms.topic: conceptual
keywords: wmf,powershell,installeren
title: PowerShell-Engine-verbeteringen in WMF 5.1
ms.openlocfilehash: 738f72b910de7d44f48309013237d523d0dd40a4
ms.sourcegitcommit: e7445ba8203da304286c591ff513900ad1c244a4
ms.translationtype: MT
ms.contentlocale: nl-NL
ms.lasthandoff: 04/23/2019
ms.locfileid: "62055561"
---
# <a name="powershell-engine-improvements"></a>Verbeteringen van de PowerShell-Engine

De volgende verbeteringen aangebracht in de engine van de PowerShell core in WMF 5.1 geïmplementeerd:

## <a name="performance"></a>Prestaties

Prestaties zijn verbeterd in enkele belangrijke gebieden:

- Opstarten
- Pipelining voor cmdlets, zoals `ForEach-Object` en `Where-Object` ongeveer 50% sneller

Aantal voorbeeld verbeteringen (uw resultaat kunnen variëren, afhankelijk van uw hardware):

| Scenario | 5.0-tijd (ms) | 5.1-tijd (ms) |
| -------- | :---------------: | :---------------: |
| `powershell -command "echo 1"` | 900 | 250 |
| Eerste ooit PowerShell uitvoeren: `powershell -command "Unknown-Command"` | 30000 | 13000 |
| Opdracht analysis-cache is gemaakt: `powershell -command "Unknown-Command"` | 7000 | 520 |
| <code>1..1000000 &#124; % { }</code> | 1400 | 750 |

> [!Note]
> Een wijziging met betrekking tot opstarten mogelijk gevolgen hebben voor enkele niet-ondersteunde scenario's.
> De bestanden niet meer worden gelezen door PowerShell `$pshome\*.ps1xml` --deze bestanden zijn geconverteerd naar C# om te voorkomen dat bepaalde bestands- en CPU-overhead van het verwerken van de XML-bestanden.
> De bestanden nog steeds aanwezig ondersteuning V2 side-by-side, dus als u de inhoud van het bestand wijzigt, heeft het geen effect op versie 5, alleen V2.
> Houd er rekening mee dat de inhoud van deze bestanden wijzigen nooit een ondersteund scenario is.

Een andere zichtbare wijzigingen is hoe PowerShell slaat de geëxporteerde opdrachten en andere informatie voor modules die zijn geïnstalleerd op een systeem.
Eerder deze cache is opgeslagen in de map `$env:LOCALAPPDATA\Microsoft\Windows\PowerShell\CommandAnalysis`.
In WMF 5.1, de cache is een enkel bestand `$env:LOCALAPPDATA\Microsoft\Windows\PowerShell\ModuleAnalysisCache`.
Zie [Module Analysis Cache](scenarios-features.md#module-analysis-cache) voor meer informatie.