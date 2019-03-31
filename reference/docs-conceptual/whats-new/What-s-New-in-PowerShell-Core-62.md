---
title: Wat is er nieuw in PowerShell Core 6.2
description: Nieuwe functies en wijzigingen die zijn uitgebracht in PowerShell Core 6.2
ms.date: 03/28/2019
ms.openlocfilehash: 2224d23a244175059a705c07001e8ad8d6ab3aa0
ms.sourcegitcommit: 8dd4394cf867005a8b9ef0bb74b744c964fbc332
ms.translationtype: MT
ms.contentlocale: nl-NL
ms.lasthandoff: 03/30/2019
ms.locfileid: "58750032"
---
# <a name="whats-new-in-powershell-core-62"></a>Wat is er nieuw in PowerShell Core 6.2

Hieronder ziet u een selectie van een aantal van de belangrijkste nieuwe functies en wijzigingen die zijn geïntroduceerd in PowerShell Core 6.2.

Er is ook **ton** van "fijne" waardoor PowerShell sneller en stabieler (plus veel en veel fouten opgelost).
Voor een volledige lijst van wijzigingen, Bekijk onze [changelog op GitHub](https://github.com/PowerShell/PowerShell/blob/master/CHANGELOG.md).

En hoewel we noemen enkele onderstaande namen, Hartelijk dank aan [alle van de community-inzenders](https://github.com/PowerShell/PowerShell/graphs/contributors) die deze versie mogelijk gemaakt.

## <a name="engine-updates-and-fixes"></a>Engine-Updates en oplossingen

- PowerShell voor externe toegang inschakelen/uitschakelen cmdlet waarschuwingsberichten toevoegen ([#9203][])
- Oplossing voor `FormatTable` externe deserialisatie regressie ([#9116][])
- Bijwerken van de taak op basis van `async` API's toegevoegd aan PowerShell om terug te keren een taakobject dat rechtstreeks ([#9079][])
- Toevoegen van 5 `InvokeAsync` overloads en `StopAsync` naar de `PowerShell` type ([#8056][]) (Bedankt @KirkMunro!)

## <a name="general-cmdlet-updates-and-fixes"></a>Algemene Cmdlet Updates en oplossingen

- Schakel `SecureString` -cmdlets voor Windows door op te slaan van de tekst zonder opmaak ([#9199][])
- Verouderd bericht toevoegen `Send-MailMessage` ([#9178][])
- Los `Restart-Computer` om te werken op `localhost` wanneer WinRM is niet aanwezig ([#9160][])
- Controleer `Start-Job` afsluitfout genereren wanneer PowerShell wordt gehost ([#9128][])
- Versie van de update voor `PowerShell.Native` en tests die als host fungeert ([#8983][])

## <a name="breaking-changes"></a>Wijzigingen die fouten veroorzaken

Los de - NoEnumerate gedrag in Write-Output moet consistent zijn met Windows PowerShell ([#9069][]) (Bedankt @vexx32!)

<!-- Link references -->
[#8056]: https://github.com/PowerShell/PowerShell/pull/8056
[#8983]: https://github.com/PowerShell/PowerShell/pull/8983
[#9069]: https://github.com/PowerShell/PowerShell/pull/9069
[#9079]: https://github.com/PowerShell/PowerShell/pull/9079
[#9116]: https://github.com/PowerShell/PowerShell/pull/9116
[#9128]: https://github.com/PowerShell/PowerShell/pull/9128
[#9160]: https://github.com/PowerShell/PowerShell/pull/9160
[#9178]: https://github.com/PowerShell/PowerShell/pull/9178
[#9199]: https://github.com/PowerShell/PowerShell/pull/9199
[#9203]: https://github.com/PowerShell/PowerShell/pull/9203
