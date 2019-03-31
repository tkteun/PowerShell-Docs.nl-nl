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
# <a name="whats-new-in-powershell-core-62"></a><span data-ttu-id="e9429-103">Wat is er nieuw in PowerShell Core 6.2</span><span class="sxs-lookup"><span data-stu-id="e9429-103">What's New in PowerShell Core 6.2</span></span>

<span data-ttu-id="e9429-104">Hieronder ziet u een selectie van een aantal van de belangrijkste nieuwe functies en wijzigingen die zijn geïntroduceerd in PowerShell Core 6.2.</span><span class="sxs-lookup"><span data-stu-id="e9429-104">Below is a selection of some of the major new features and changes that have been introduced in PowerShell Core 6.2.</span></span>

<span data-ttu-id="e9429-105">Er is ook **ton** van "fijne" waardoor PowerShell sneller en stabieler (plus veel en veel fouten opgelost).</span><span class="sxs-lookup"><span data-stu-id="e9429-105">There's also **tons** of "boring stuff" that make PowerShell faster and more stable (plus lots and lots of bug fixes)!</span></span>
<span data-ttu-id="e9429-106">Voor een volledige lijst van wijzigingen, Bekijk onze [changelog op GitHub](https://github.com/PowerShell/PowerShell/blob/master/CHANGELOG.md).</span><span class="sxs-lookup"><span data-stu-id="e9429-106">For a full list of changes, check out our [changelog on GitHub](https://github.com/PowerShell/PowerShell/blob/master/CHANGELOG.md).</span></span>

<span data-ttu-id="e9429-107">En hoewel we noemen enkele onderstaande namen, Hartelijk dank aan [alle van de community-inzenders](https://github.com/PowerShell/PowerShell/graphs/contributors) die deze versie mogelijk gemaakt.</span><span class="sxs-lookup"><span data-stu-id="e9429-107">And while we call out some names below, thank you to [all of the community contributors](https://github.com/PowerShell/PowerShell/graphs/contributors) that made this release possible.</span></span>

## <a name="engine-updates-and-fixes"></a><span data-ttu-id="e9429-108">Engine-Updates en oplossingen</span><span class="sxs-lookup"><span data-stu-id="e9429-108">Engine Updates and Fixes</span></span>

- <span data-ttu-id="e9429-109">PowerShell voor externe toegang inschakelen/uitschakelen cmdlet waarschuwingsberichten toevoegen ([#9203][])</span><span class="sxs-lookup"><span data-stu-id="e9429-109">Add PowerShell remoting enable/disable cmdlet warning messages ([#9203][])</span></span>
- <span data-ttu-id="e9429-110">Oplossing voor `FormatTable` externe deserialisatie regressie ([#9116][])</span><span class="sxs-lookup"><span data-stu-id="e9429-110">Fix for `FormatTable` remote deserialization regression ([#9116][])</span></span>
- <span data-ttu-id="e9429-111">Bijwerken van de taak op basis van `async` API's toegevoegd aan PowerShell om terug te keren een taakobject dat rechtstreeks ([#9079][])</span><span class="sxs-lookup"><span data-stu-id="e9429-111">Update the task-based `async` APIs added to PowerShell to return a Task object directly ([#9079][])</span></span>
- <span data-ttu-id="e9429-112">Toevoegen van 5 `InvokeAsync` overloads en `StopAsync` naar de `PowerShell` type ([#8056][]) (Bedankt @KirkMunro!)</span><span class="sxs-lookup"><span data-stu-id="e9429-112">Add 5 `InvokeAsync` overloads and `StopAsync` to the `PowerShell` type ([#8056][]) (Thanks @KirkMunro!)</span></span>

## <a name="general-cmdlet-updates-and-fixes"></a><span data-ttu-id="e9429-113">Algemene Cmdlet Updates en oplossingen</span><span class="sxs-lookup"><span data-stu-id="e9429-113">General Cmdlet Updates and Fixes</span></span>

- <span data-ttu-id="e9429-114">Schakel `SecureString` -cmdlets voor Windows door op te slaan van de tekst zonder opmaak ([#9199][])</span><span class="sxs-lookup"><span data-stu-id="e9429-114">Enable `SecureString` cmdlets for non-Windows by storing the plain text ([#9199][])</span></span>
- <span data-ttu-id="e9429-115">Verouderd bericht toevoegen `Send-MailMessage` ([#9178][])</span><span class="sxs-lookup"><span data-stu-id="e9429-115">Add Obsolete message to `Send-MailMessage` ([#9178][])</span></span>
- <span data-ttu-id="e9429-116">Los `Restart-Computer` om te werken op `localhost` wanneer WinRM is niet aanwezig ([#9160][])</span><span class="sxs-lookup"><span data-stu-id="e9429-116">Fix `Restart-Computer` to work on `localhost` when WinRM is not present ([#9160][])</span></span>
- <span data-ttu-id="e9429-117">Controleer `Start-Job` afsluitfout genereren wanneer PowerShell wordt gehost ([#9128][])</span><span class="sxs-lookup"><span data-stu-id="e9429-117">Make `Start-Job` throw terminating error when PowerShell is being hosted ([#9128][])</span></span>
- <span data-ttu-id="e9429-118">Versie van de update voor `PowerShell.Native` en tests die als host fungeert ([#8983][])</span><span class="sxs-lookup"><span data-stu-id="e9429-118">Update version for `PowerShell.Native` and hosting tests ([#8983][])</span></span>

## <a name="breaking-changes"></a><span data-ttu-id="e9429-119">Wijzigingen die fouten veroorzaken</span><span class="sxs-lookup"><span data-stu-id="e9429-119">Breaking Changes</span></span>

<span data-ttu-id="e9429-120">Los de - NoEnumerate gedrag in Write-Output moet consistent zijn met Windows PowerShell ([#9069][]) (Bedankt @vexx32!)</span><span class="sxs-lookup"><span data-stu-id="e9429-120">Fix -NoEnumerate behavior in Write-Output to be consistent with Windows PowerShell ([#9069][]) (Thanks @vexx32!)</span></span>

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
