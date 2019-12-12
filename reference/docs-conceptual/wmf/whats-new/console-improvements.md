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
# <a name="console-improvements-in-wmf-51"></a><span data-ttu-id="fce46-103">Verbeteringen van de console in WMF 5.1</span><span class="sxs-lookup"><span data-stu-id="fce46-103">Console Improvements in WMF 5.1</span></span>

## <a name="powershell-console-improvements"></a><span data-ttu-id="fce46-104">Verbeteringen in de Power shell-console</span><span class="sxs-lookup"><span data-stu-id="fce46-104">PowerShell console improvements</span></span>

<span data-ttu-id="fce46-105">De volgende wijzigingen zijn aangebracht in Power shell. exe in WMF 5,1 om de console-ervaring te verbeteren:</span><span class="sxs-lookup"><span data-stu-id="fce46-105">The following changes have been made to powershell.exe in WMF 5.1 to improve the console experience:</span></span>

### <a name="vt100-support"></a><span data-ttu-id="fce46-106">VT100-ondersteuning</span><span class="sxs-lookup"><span data-stu-id="fce46-106">VT100 support</span></span>

<span data-ttu-id="fce46-107">Windows 10 heeft ondersteuning toegevoegd voor [VT100-escape reeksen](/windows/console/console-virtual-terminal-sequences).</span><span class="sxs-lookup"><span data-stu-id="fce46-107">Windows 10 added support for [VT100 escape sequences](/windows/console/console-virtual-terminal-sequences).</span></span>
<span data-ttu-id="fce46-108">In Power shell worden bepaalde escape reeksen voor VT100-opmaak genegeerd bij het berekenen van tabel breedten.</span><span class="sxs-lookup"><span data-stu-id="fce46-108">PowerShell will ignore certain VT100 formatting escape sequences when calculating table widths.</span></span>

<span data-ttu-id="fce46-109">Power Shell heeft ook een nieuwe API toegevoegd die in opmaak code kan worden gebruikt om te bepalen of VT100 wordt ondersteund.</span><span class="sxs-lookup"><span data-stu-id="fce46-109">PowerShell also added a new API that can be used in formatting code to determine if VT100 is supported.</span></span> <span data-ttu-id="fce46-110">Bijvoorbeeld:</span><span class="sxs-lookup"><span data-stu-id="fce46-110">For example:</span></span>

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

<span data-ttu-id="fce46-111">Hier volgt een volledig [voor beeld](https://gist.github.com/lzybkr/dcb973dccd54900b67783c48083c28f7) dat kan worden gebruikt om overeenkomsten van `Select-String`te markeren.</span><span class="sxs-lookup"><span data-stu-id="fce46-111">Here is a complete [example](https://gist.github.com/lzybkr/dcb973dccd54900b67783c48083c28f7) that can be used to highlight matches from `Select-String`.</span></span> <span data-ttu-id="fce46-112">Sla het voor beeld op in een bestand met de naam `MatchInfo.format.ps1xml`en gebruik het vervolgens in uw profiel of ergens anders en voer `Update-FormatData -Prepend MatchInfo.format.ps1xml`uit.</span><span class="sxs-lookup"><span data-stu-id="fce46-112">Save the example in a file named `MatchInfo.format.ps1xml`, then to use it, in your profile or elsewhere, run `Update-FormatData -Prepend MatchInfo.format.ps1xml`.</span></span>

<span data-ttu-id="fce46-113">Houd er rekening mee dat VT100-escape reeksen alleen worden ondersteund vanaf de Windows 10 jubileum update.</span><span class="sxs-lookup"><span data-stu-id="fce46-113">Note that VT100 escape sequences are only supported starting with the Windows 10 Anniversary update.</span></span>
<span data-ttu-id="fce46-114">Ze worden niet ondersteund op eerdere systemen.</span><span class="sxs-lookup"><span data-stu-id="fce46-114">They are not supported on earlier systems.</span></span>

### <a name="vi-mode-support-in-psreadline"></a><span data-ttu-id="fce46-115">Ondersteuning voor de VI-modus in PSReadline</span><span class="sxs-lookup"><span data-stu-id="fce46-115">Vi mode support in PSReadline</span></span>

<span data-ttu-id="fce46-116">[PSReadline](https://github.com/PowerShell/PSReadLine) voegt ondersteuning toe voor de modus voor VI.</span><span class="sxs-lookup"><span data-stu-id="fce46-116">[PSReadline](https://github.com/PowerShell/PSReadLine) adds support for vi mode.</span></span> <span data-ttu-id="fce46-117">Als u de modus VI wilt gebruiken, voert u `Set-PSReadlineOption -EditMode Vi`uit.</span><span class="sxs-lookup"><span data-stu-id="fce46-117">To use vi mode, run `Set-PSReadlineOption -EditMode Vi`.</span></span>

### <a name="redirected-stdin-with-interactive-input"></a><span data-ttu-id="fce46-118">Omgeleide stdin met interactieve invoer</span><span class="sxs-lookup"><span data-stu-id="fce46-118">Redirected stdin with interactive input</span></span>

<span data-ttu-id="fce46-119">In eerdere versies was het starten van Power shell met `powershell -File -` vereist toen stdin werd omgeleid en wilt u opdrachten interactief invoeren.</span><span class="sxs-lookup"><span data-stu-id="fce46-119">In earlier versions, starting PowerShell with `powershell -File -` was required when stdin was redirected and you wanted to enter commands interactively.</span></span>

<span data-ttu-id="fce46-120">Met WMF 5,1 is deze optie moeilijk te detecteren niet meer nodig.</span><span class="sxs-lookup"><span data-stu-id="fce46-120">With WMF 5.1, this hard to discover option is no longer necessary.</span></span> <span data-ttu-id="fce46-121">U kunt Power shell zonder opties starten.</span><span class="sxs-lookup"><span data-stu-id="fce46-121">You can start PowerShell without any options.</span></span>

<span data-ttu-id="fce46-122">Houd er rekening mee dat PSReadline geen ondersteuning biedt voor omgeleide stdin en dat de ingebouwde opdracht regel functie voor het bewerken van een omgeleide stdin een zeer beperkt aantal, bijvoorbeeld pijl toetsen niet werkt.</span><span class="sxs-lookup"><span data-stu-id="fce46-122">Note that PSReadline does not support redirected stdin, and the built-in command-line editing experience with redirected stdin is extremely limited, for example, arrow keys don't work.</span></span> <span data-ttu-id="fce46-123">Een toekomstige release van PSReadline moet dit probleem oplossen.</span><span class="sxs-lookup"><span data-stu-id="fce46-123">A future release of PSReadline should address this issue.</span></span>