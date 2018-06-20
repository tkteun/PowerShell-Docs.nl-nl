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
# <a name="console-improvements-in-wmf-51"></a><span data-ttu-id="bf946-103">Verbeteringen in de beheerconsole in WMF 5.1#</span><span class="sxs-lookup"><span data-stu-id="bf946-103">Console Improvements in WMF 5.1#</span></span>

## <a name="powershell-console-improvements"></a><span data-ttu-id="bf946-104">Verbeteringen in de beheerconsole PowerShell</span><span class="sxs-lookup"><span data-stu-id="bf946-104">PowerShell console improvements</span></span>

<span data-ttu-id="bf946-105">De volgende wijzigingen zijn aangebracht aan powershell.exe in WMF 5.1 om de console-ervaring te verbeteren:</span><span class="sxs-lookup"><span data-stu-id="bf946-105">The following changes have been made to powershell.exe in WMF 5.1 to improve the console experience:</span></span>

###<a name="vt100-support"></a><span data-ttu-id="bf946-106">VT100-ondersteuning</span><span class="sxs-lookup"><span data-stu-id="bf946-106">VT100 support</span></span>

<span data-ttu-id="bf946-107">Windows 10 is ondersteuning toegevoegd voor [VT100 escapereeksen](https://msdn.microsoft.com/en-us/library/windows/desktop/mt638032(v=vs.85).aspx).</span><span class="sxs-lookup"><span data-stu-id="bf946-107">Windows 10 added support for [VT100 escape sequences](https://msdn.microsoft.com/en-us/library/windows/desktop/mt638032(v=vs.85).aspx).</span></span>
<span data-ttu-id="bf946-108">PowerShell worden bepaalde VT100 opmaak escapereeksen genegeerd bij het berekenen van de Tabelbreedten.</span><span class="sxs-lookup"><span data-stu-id="bf946-108">PowerShell will ignore certain VT100 formatting escape sequences when calculating table widths.</span></span>

<span data-ttu-id="bf946-109">PowerShell toegevoegd ook een nieuwe API die kan worden gebruikt in de opmaak opgeven om te bepalen of VT100 wordt ondersteund.</span><span class="sxs-lookup"><span data-stu-id="bf946-109">PowerShell also added a new API that can be used in formatting code to determine if VT100 is supported.</span></span>
<span data-ttu-id="bf946-110">Bijvoorbeeld:</span><span class="sxs-lookup"><span data-stu-id="bf946-110">For example:</span></span>

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
<span data-ttu-id="bf946-111">Hier volgt een volledige [voorbeeld](https://gist.github.com/lzybkr/dcb973dccd54900b67783c48083c28f7) die kunnen worden gebruikt om te markeren overeenkomsten uit de Select-tekenreeks.</span><span class="sxs-lookup"><span data-stu-id="bf946-111">Here is a complete [example](https://gist.github.com/lzybkr/dcb973dccd54900b67783c48083c28f7) that can be used to highlight matches from Select-String.</span></span>
<span data-ttu-id="bf946-112">Opslaan van het voorbeeld in een bestand met de naam `MatchInfo.format.ps1xml`, voert u voor het gebruik ervan in uw profiel of elders, `Update-FormatData -Prepend MatchInfo.format.ps1xml`.</span><span class="sxs-lookup"><span data-stu-id="bf946-112">Save the example in a file named `MatchInfo.format.ps1xml`, then to use it, in your profile or elsewhere, run `Update-FormatData -Prepend MatchInfo.format.ps1xml`.</span></span>

<span data-ttu-id="bf946-113">Houd er rekening mee dat VT100 escapereeksen worden alleen ondersteund met de update voor Windows 10 Verjaardag; starten ze worden niet ondersteund op oudere systemen.</span><span class="sxs-lookup"><span data-stu-id="bf946-113">Note that VT100 escape sequences are only supported starting with the Windows 10 Anniversary update; they are not supported on earlier systems.</span></span>

### <a name="vi-mode-support-in-psreadline"></a><span data-ttu-id="bf946-114">Ondersteuning voor VI-modus in PSReadline</span><span class="sxs-lookup"><span data-stu-id="bf946-114">Vi mode support in PSReadline</span></span>

<span data-ttu-id="bf946-115">[PSReadline](https://github.com/lzybkr/PSReadLine) voegt ondersteuning toe voor vi-modus.</span><span class="sxs-lookup"><span data-stu-id="bf946-115">[PSReadline](https://github.com/lzybkr/PSReadLine) adds support for vi mode.</span></span> <span data-ttu-id="bf946-116">Voer om vi modus gebruiken `Set-PSReadlineOption -EditMode Vi`.</span><span class="sxs-lookup"><span data-stu-id="bf946-116">To use vi mode, run `Set-PSReadlineOption -EditMode Vi`.</span></span>

### <a name="redirected-stdin-with-interactive-input"></a><span data-ttu-id="bf946-117">Omgeleide stdin met interactieve invoer</span><span class="sxs-lookup"><span data-stu-id="bf946-117">Redirected stdin with interactive input</span></span>

<span data-ttu-id="bf946-118">In eerdere versies, PowerShell met vanaf `powershell -File -` is vereist wanneer stdin is omgeleid en u wilt voert opdrachten interactief.</span><span class="sxs-lookup"><span data-stu-id="bf946-118">In earlier versions, starting PowerShell with `powershell -File -` was required when stdin was redirected and you wanted to enter commands interactively.</span></span>

<span data-ttu-id="bf946-119">Met WMF 5.1, dit moeilijk te detecteren optie is niet meer nodig.</span><span class="sxs-lookup"><span data-stu-id="bf946-119">With WMF 5.1, this hard to discover option is no longer necessary.</span></span>
<span data-ttu-id="bf946-120">U kunt PowerShell starten zonder opties, zoals `powershell`.</span><span class="sxs-lookup"><span data-stu-id="bf946-120">You can start PowerShell without any options, e.g. `powershell`.</span></span>

<span data-ttu-id="bf946-121">Let op: PSReadline biedt momenteel geen ondersteuning voor omgeleid stdin, en de ingebouwde opdrachtregel bewerken ervaring met omgeleide stdin is zeer beperkt, bijvoorbeeld pijltoetsen werken niet.</span><span class="sxs-lookup"><span data-stu-id="bf946-121">Note that PSReadline does not currently support redirected stdin, and the built-in command-line editing experience with redirected stdin is extremely limited, for example, arrow keys don't work.</span></span>
<span data-ttu-id="bf946-122">Een toekomstige release van PSReadline moet dit probleem kunt oplossen.</span><span class="sxs-lookup"><span data-stu-id="bf946-122">A future release of PSReadline should address this issue.</span></span>
