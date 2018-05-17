---
ms.date: 06/12/2017
ms.topic: conceptual
keywords: wmf,powershell,installeren
title: PowerShell-Engine verbeteringen in WMF 5.1
ms.openlocfilehash: 98095904157a675bbe84616b1d9cbb22689cd059
ms.sourcegitcommit: 54534635eedacf531d8d6344019dc16a50b8b441
ms.translationtype: MT
ms.contentlocale: nl-NL
ms.lasthandoff: 05/17/2018
---
#<a name="powershell-engine-improvements"></a>Verbeteringen van de PowerShell-Engine

De volgende verbeteringen aangebracht in de kern PowerShell-engine in WMF 5.1 geïmplementeerd:


## <a name="performance"></a>Prestaties ##

Prestaties verbeterd in enkele belangrijke gebieden:

- Opstarten
- Pipelining naar cmdlets zoals ForEach-Object en Where-Object is ongeveer 50% sneller

Enkele voorbeeld-verbeteringen (uw resultaten kunnen variëren, afhankelijk van uw hardware):

| Scenario | 5.0-tijd (ms) | 5.1-tijd (ms) |
| -------- | :---------------: | :---------------: |
| `powershell -command "echo 1"` | 900 | 250 |
| Eerste ooit PowerShell uitvoeren: `powershell -command "Unknown-Command"` | 30000 | 13000 |
| Opdracht analysis-cache is gebouwd: `powershell -command "Unknown-Command"` | 7000 | 520 |
| <code>1..1000000 &#124; % { }</code> | 1400 | 750 |

> Opmerking één wijziging betrekking hebben op het starten van de mogelijk gevolgen hebben voor een aantal niet-ondersteunde scenario's.
> De bestanden niet meer worden gelezen door PowerShell `$pshome\*.ps1xml` --deze bestanden zijn geconverteerd naar C# om te voorkomen dat een bestand en CPU-overhead van de verwerking van de XML-bestanden.
De bestanden nog steeds aanwezig voor ondersteuning van V2 side-by-side, dus als u de inhoud van het bestand wijzigt, heeft deze geen effect op V5, alleen V2.
Houd er rekening mee dat de inhoud van deze bestanden wijzigen nooit een ondersteund scenario is.

Een andere zichtbare wijzigingen is hoe PowerShell slaat de geëxporteerde opdrachten en andere informatie voor modules die zijn geïnstalleerd op een systeem.
Voorheen werd door deze cache is opgeslagen in de map `$env:LOCALAPPDATA\Microsoft\Windows\PowerShell\CommandAnalysis`.
In WMF 5.1, de cache is een enkel bestand `$env:LOCALAPPDATA\Microsoft\Windows\PowerShell\ModuleAnalysisCache`.
Zie [Module Analysis Cache](scenarios-features.md#module-analysis-cache) voor meer informatie.
