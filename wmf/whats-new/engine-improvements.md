---
ms.date: 06/12/2017
ms.topic: conceptual
keywords: wmf,powershell,installeren
title: PowerShell-Engine-verbeteringen in WMF 5.1
ms.openlocfilehash: a0af702832c0a90c994650e25918ecacdc33fc4b
ms.sourcegitcommit: 01b81317029b28dd9b61d167045fd31f1ec7bc06
ms.translationtype: MT
ms.contentlocale: nl-NL
ms.lasthandoff: 05/17/2019
ms.locfileid: "65856180"
---
# <a name="powershell-engine-improvements"></a><span data-ttu-id="68098-103">Verbeteringen van de PowerShell-Engine</span><span class="sxs-lookup"><span data-stu-id="68098-103">PowerShell Engine Improvements</span></span>

<span data-ttu-id="68098-104">De volgende verbeteringen aangebracht in de engine van de PowerShell core in WMF 5.1 geïmplementeerd:</span><span class="sxs-lookup"><span data-stu-id="68098-104">The following improvements to the core PowerShell engine have been implemented in WMF 5.1:</span></span>

## <a name="performance"></a><span data-ttu-id="68098-105">Prestaties</span><span class="sxs-lookup"><span data-stu-id="68098-105">Performance</span></span>

<span data-ttu-id="68098-106">Prestaties zijn verbeterd in enkele belangrijke gebieden:</span><span class="sxs-lookup"><span data-stu-id="68098-106">Performance has improved in some important areas:</span></span>

- <span data-ttu-id="68098-107">Opstarten</span><span class="sxs-lookup"><span data-stu-id="68098-107">Startup</span></span>
- <span data-ttu-id="68098-108">Pipelining voor cmdlets, zoals `ForEach-Object` en `Where-Object` ongeveer 50% sneller</span><span class="sxs-lookup"><span data-stu-id="68098-108">Pipelining to cmdlets like `ForEach-Object` and `Where-Object` is approximately 50% faster</span></span>

<span data-ttu-id="68098-109">Aantal voorbeeld verbeteringen (uw resultaat kunnen variëren, afhankelijk van uw hardware):</span><span class="sxs-lookup"><span data-stu-id="68098-109">Some example improvements (your results may vary depending on your hardware):</span></span>

| <span data-ttu-id="68098-110">Scenario</span><span class="sxs-lookup"><span data-stu-id="68098-110">Scenario</span></span> | <span data-ttu-id="68098-111">5.0-tijd (ms)</span><span class="sxs-lookup"><span data-stu-id="68098-111">5.0 Time (ms)</span></span> | <span data-ttu-id="68098-112">5.1-tijd (ms)</span><span class="sxs-lookup"><span data-stu-id="68098-112">5.1 Time (ms)</span></span> |
| -------- | :---------------: | :---------------: |
| `powershell -command "echo 1"` | <span data-ttu-id="68098-113">900</span><span class="sxs-lookup"><span data-stu-id="68098-113">900</span></span> | <span data-ttu-id="68098-114">250</span><span class="sxs-lookup"><span data-stu-id="68098-114">250</span></span> |
| <span data-ttu-id="68098-115">Eerste ooit PowerShell uitvoeren: `powershell -command "Unknown-Command"`</span><span class="sxs-lookup"><span data-stu-id="68098-115">First ever PowerShell run: `powershell -command "Unknown-Command"`</span></span> | <span data-ttu-id="68098-116">30000</span><span class="sxs-lookup"><span data-stu-id="68098-116">30000</span></span> | <span data-ttu-id="68098-117">13000</span><span class="sxs-lookup"><span data-stu-id="68098-117">13000</span></span> |
| <span data-ttu-id="68098-118">Opdracht analysis-cache is gemaakt: `powershell -command "Unknown-Command"`</span><span class="sxs-lookup"><span data-stu-id="68098-118">Command analysis cache built: `powershell -command "Unknown-Command"`</span></span> | <span data-ttu-id="68098-119">7000</span><span class="sxs-lookup"><span data-stu-id="68098-119">7000</span></span> | <span data-ttu-id="68098-120">520</span><span class="sxs-lookup"><span data-stu-id="68098-120">520</span></span> |
| <code>1..1000000 &#124; % { }</code> | <span data-ttu-id="68098-121">1400</span><span class="sxs-lookup"><span data-stu-id="68098-121">1400</span></span> | <span data-ttu-id="68098-122">750</span><span class="sxs-lookup"><span data-stu-id="68098-122">750</span></span> |

> [!NOTE]
> <span data-ttu-id="68098-123">Een wijziging met betrekking tot opstarten mogelijk gevolgen hebben voor enkele niet-ondersteunde scenario's.</span><span class="sxs-lookup"><span data-stu-id="68098-123">One change related to startup might impact some unsupported scenarios.</span></span> <span data-ttu-id="68098-124">De bestanden niet meer worden gelezen door PowerShell `$pshome\*.ps1xml` --deze bestanden zijn geconverteerd naar C# om te voorkomen dat bepaalde bestands- en CPU-overhead van het verwerken van de XML-bestanden.</span><span class="sxs-lookup"><span data-stu-id="68098-124">PowerShell no longer reads the files `$pshome\*.ps1xml` -- these files have been converted to C# to avoid some file and CPU overhead of processing the XML files.</span></span> <span data-ttu-id="68098-125">De bestanden nog steeds aanwezig ondersteuning V2 side-by-side, dus als u de inhoud van het bestand wijzigt, heeft het geen effect op versie 5, alleen V2.</span><span class="sxs-lookup"><span data-stu-id="68098-125">The files still exist to support V2 side-by-side, so if you change the file contents, it will not have any effect to V5, only V2.</span></span> <span data-ttu-id="68098-126">Houd er rekening mee dat de inhoud van deze bestanden wijzigen nooit een ondersteund scenario is.</span><span class="sxs-lookup"><span data-stu-id="68098-126">Note that changing the contents of these files was never a supported scenario.</span></span>

<span data-ttu-id="68098-127">Een andere zichtbare wijzigingen is hoe PowerShell slaat de geëxporteerde opdrachten en andere informatie voor modules die zijn geïnstalleerd op een systeem.</span><span class="sxs-lookup"><span data-stu-id="68098-127">Another visible change is how PowerShell caches the exported commands and other information for modules that are installed on a system.</span></span> <span data-ttu-id="68098-128">Eerder deze cache is opgeslagen in de map `$env:LOCALAPPDATA\Microsoft\Windows\PowerShell\CommandAnalysis`.</span><span class="sxs-lookup"><span data-stu-id="68098-128">Previously, this cache was stored in the directory `$env:LOCALAPPDATA\Microsoft\Windows\PowerShell\CommandAnalysis`.</span></span> <span data-ttu-id="68098-129">In WMF 5.1, de cache is een enkel bestand `$env:LOCALAPPDATA\Microsoft\Windows\PowerShell\ModuleAnalysisCache`.</span><span class="sxs-lookup"><span data-stu-id="68098-129">In WMF 5.1, the cache is a single file `$env:LOCALAPPDATA\Microsoft\Windows\PowerShell\ModuleAnalysisCache`.</span></span> <span data-ttu-id="68098-130">Zie [Module Analysis Cache](release-notes.md#module-analysis-cache) voor meer informatie.</span><span class="sxs-lookup"><span data-stu-id="68098-130">See [Module Analysis Cache](release-notes.md#module-analysis-cache) for more details.</span></span>