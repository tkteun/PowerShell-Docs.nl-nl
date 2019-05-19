---
ms.date: 06/12/2017
keywords: wmf,powershell,installeren
title: Verbeteringen in de console in WMF 5.1
ms.openlocfilehash: d0dd8e3c31dc0ddebab1bb899468b77a9292954d
ms.sourcegitcommit: 01b81317029b28dd9b61d167045fd31f1ec7bc06
ms.translationtype: MT
ms.contentlocale: nl-NL
ms.lasthandoff: 05/17/2019
ms.locfileid: "65856215"
---
# <a name="console-improvements-in-wmf-51"></a><span data-ttu-id="e5d6c-103">Verbeteringen in de console in WMF 5.1</span><span class="sxs-lookup"><span data-stu-id="e5d6c-103">Console Improvements in WMF 5.1</span></span>

## <a name="powershell-console-improvements"></a><span data-ttu-id="e5d6c-104">Verbeteringen in de console van PowerShell</span><span class="sxs-lookup"><span data-stu-id="e5d6c-104">PowerShell console improvements</span></span>

<span data-ttu-id="e5d6c-105">De volgende wijzigingen zijn aangebracht naar powershell.exe in WMF 5.1 om de console-ervaring te verbeteren:</span><span class="sxs-lookup"><span data-stu-id="e5d6c-105">The following changes have been made to powershell.exe in WMF 5.1 to improve the console experience:</span></span>

### <a name="vt100-support"></a><span data-ttu-id="e5d6c-106">Ondersteuning voor VT100</span><span class="sxs-lookup"><span data-stu-id="e5d6c-106">VT100 support</span></span>

<span data-ttu-id="e5d6c-107">Windows 10 is ondersteuning toegevoegd voor [VT100 escapereeksen](/windows/console/console-virtual-terminal-sequences).</span><span class="sxs-lookup"><span data-stu-id="e5d6c-107">Windows 10 added support for [VT100 escape sequences](/windows/console/console-virtual-terminal-sequences).</span></span>
<span data-ttu-id="e5d6c-108">PowerShell worden bepaalde VT100 opmaak escapereeksen genegeerd bij het berekenen van de tabelbreedte van de.</span><span class="sxs-lookup"><span data-stu-id="e5d6c-108">PowerShell will ignore certain VT100 formatting escape sequences when calculating table widths.</span></span>

<span data-ttu-id="e5d6c-109">PowerShell toegevoegd ook een nieuwe API die kan worden gebruikt in de opmaak van code om te bepalen of VT100 wordt ondersteund.</span><span class="sxs-lookup"><span data-stu-id="e5d6c-109">PowerShell also added a new API that can be used in formatting code to determine if VT100 is supported.</span></span> <span data-ttu-id="e5d6c-110">Bijvoorbeeld:</span><span class="sxs-lookup"><span data-stu-id="e5d6c-110">For example:</span></span>

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

<span data-ttu-id="e5d6c-111">Dit is een complete [voorbeeld](https://gist.github.com/lzybkr/dcb973dccd54900b67783c48083c28f7) kunnen worden gebruikt voor het markeren van treffers van `Select-String`.</span><span class="sxs-lookup"><span data-stu-id="e5d6c-111">Here is a complete [example](https://gist.github.com/lzybkr/dcb973dccd54900b67783c48083c28f7) that can be used to highlight matches from `Select-String`.</span></span> <span data-ttu-id="e5d6c-112">Opslaan van het voorbeeld in een bestand met de naam `MatchInfo.format.ps1xml`, voert u als u wilt gebruiken, in uw profiel of ergens anders, `Update-FormatData -Prepend MatchInfo.format.ps1xml`.</span><span class="sxs-lookup"><span data-stu-id="e5d6c-112">Save the example in a file named `MatchInfo.format.ps1xml`, then to use it, in your profile or elsewhere, run `Update-FormatData -Prepend MatchInfo.format.ps1xml`.</span></span>

<span data-ttu-id="e5d6c-113">Houd er rekening mee dat VT100 escapereeksen worden alleen ondersteund vanaf de Windows 10 Verjaardag update.</span><span class="sxs-lookup"><span data-stu-id="e5d6c-113">Note that VT100 escape sequences are only supported starting with the Windows 10 Anniversary update.</span></span>
<span data-ttu-id="e5d6c-114">Ze worden niet ondersteund op oudere systemen.</span><span class="sxs-lookup"><span data-stu-id="e5d6c-114">They are not supported on earlier systems.</span></span>

### <a name="vi-mode-support-in-psreadline"></a><span data-ttu-id="e5d6c-115">Ondersteuning voor VI-modus in PSReadline</span><span class="sxs-lookup"><span data-stu-id="e5d6c-115">Vi mode support in PSReadline</span></span>

<span data-ttu-id="e5d6c-116">[PSReadline](https://github.com/PowerShell/PSReadLine) voegt ondersteuning toe voor vi-modus.</span><span class="sxs-lookup"><span data-stu-id="e5d6c-116">[PSReadline](https://github.com/PowerShell/PSReadLine) adds support for vi mode.</span></span> <span data-ttu-id="e5d6c-117">Voor het gebruik van vi modus uitvoeren `Set-PSReadlineOption -EditMode Vi`.</span><span class="sxs-lookup"><span data-stu-id="e5d6c-117">To use vi mode, run `Set-PSReadlineOption -EditMode Vi`.</span></span>

### <a name="redirected-stdin-with-interactive-input"></a><span data-ttu-id="e5d6c-118">Omgeleide stdin met interactieve invoer</span><span class="sxs-lookup"><span data-stu-id="e5d6c-118">Redirected stdin with interactive input</span></span>

<span data-ttu-id="e5d6c-119">In eerdere versies, PowerShell met starten `powershell -File -` is vereist wanneer stdin is omgeleid en u wilt opdrachten interactief invoeren.</span><span class="sxs-lookup"><span data-stu-id="e5d6c-119">In earlier versions, starting PowerShell with `powershell -File -` was required when stdin was redirected and you wanted to enter commands interactively.</span></span>

<span data-ttu-id="e5d6c-120">Met WMF 5.1, dit moeilijk te detecteren optie is niet meer nodig.</span><span class="sxs-lookup"><span data-stu-id="e5d6c-120">With WMF 5.1, this hard to discover option is no longer necessary.</span></span> <span data-ttu-id="e5d6c-121">U kunt PowerShell starten zonder opties.</span><span class="sxs-lookup"><span data-stu-id="e5d6c-121">You can start PowerShell without any options.</span></span>

<span data-ttu-id="e5d6c-122">Houd er rekening mee dat PSReadline biedt geen ondersteuning voor omgeleid stdin, en de ingebouwde opdrachtregel bewerken ervaring met omgeleide stdin is zeer beperkte, bijvoorbeeld pijltoetsen werken niet.</span><span class="sxs-lookup"><span data-stu-id="e5d6c-122">Note that PSReadline does not support redirected stdin, and the built-in command-line editing experience with redirected stdin is extremely limited, for example, arrow keys don't work.</span></span> <span data-ttu-id="e5d6c-123">Een toekomstige release van PSReadline moet dit probleem oplossen.</span><span class="sxs-lookup"><span data-stu-id="e5d6c-123">A future release of PSReadline should address this issue.</span></span>