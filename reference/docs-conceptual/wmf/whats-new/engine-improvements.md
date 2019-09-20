---
ms.date: 06/12/2017
ms.topic: conceptual
keywords: wmf,powershell,installeren
title: Verbeteringen van PowerShell-engine in WMF 5.1
ms.openlocfilehash: a0af702832c0a90c994650e25918ecacdc33fc4b
ms.sourcegitcommit: 0a6b562a497860caadba754c75a83215315d37a1
ms.translationtype: MT
ms.contentlocale: nl-NL
ms.lasthandoff: 09/19/2019
ms.locfileid: "71145066"
---
# <a name="powershell-engine-improvements"></a><span data-ttu-id="9d32e-103">Verbeteringen in Power shell-engine</span><span class="sxs-lookup"><span data-stu-id="9d32e-103">PowerShell Engine Improvements</span></span>

<span data-ttu-id="9d32e-104">De volgende verbeteringen voor de kern-Power shell-Engine zijn geïmplementeerd in WMF 5,1:</span><span class="sxs-lookup"><span data-stu-id="9d32e-104">The following improvements to the core PowerShell engine have been implemented in WMF 5.1:</span></span>

## <a name="performance"></a><span data-ttu-id="9d32e-105">Prestaties</span><span class="sxs-lookup"><span data-stu-id="9d32e-105">Performance</span></span>

<span data-ttu-id="9d32e-106">Prestaties zijn verbeterd op enkele belang rijke gebieden:</span><span class="sxs-lookup"><span data-stu-id="9d32e-106">Performance has improved in some important areas:</span></span>

- <span data-ttu-id="9d32e-107">Opstarten</span><span class="sxs-lookup"><span data-stu-id="9d32e-107">Startup</span></span>
- <span data-ttu-id="9d32e-108">Pipelinen naar cmdlets zoals `ForEach-Object` en `Where-Object` is ongeveer 50% sneller</span><span class="sxs-lookup"><span data-stu-id="9d32e-108">Pipelining to cmdlets like `ForEach-Object` and `Where-Object` is approximately 50% faster</span></span>

<span data-ttu-id="9d32e-109">Enkele voor beelden van verbeteringen (uw resultaten kunnen variëren, afhankelijk van uw hardware):</span><span class="sxs-lookup"><span data-stu-id="9d32e-109">Some example improvements (your results may vary depending on your hardware):</span></span>

| <span data-ttu-id="9d32e-110">Scenario</span><span class="sxs-lookup"><span data-stu-id="9d32e-110">Scenario</span></span> | <span data-ttu-id="9d32e-111">5,0 tijd (MS)</span><span class="sxs-lookup"><span data-stu-id="9d32e-111">5.0 Time (ms)</span></span> | <span data-ttu-id="9d32e-112">5,1 tijd (MS)</span><span class="sxs-lookup"><span data-stu-id="9d32e-112">5.1 Time (ms)</span></span> |
| -------- | :---------------: | :---------------: |
| `powershell -command "echo 1"` | <span data-ttu-id="9d32e-113">900</span><span class="sxs-lookup"><span data-stu-id="9d32e-113">900</span></span> | <span data-ttu-id="9d32e-114">250</span><span class="sxs-lookup"><span data-stu-id="9d32e-114">250</span></span> |
| <span data-ttu-id="9d32e-115">Eerste keer dat Power shell wordt uitgevoerd:`powershell -command "Unknown-Command"`</span><span class="sxs-lookup"><span data-stu-id="9d32e-115">First ever PowerShell run: `powershell -command "Unknown-Command"`</span></span> | <span data-ttu-id="9d32e-116">30000</span><span class="sxs-lookup"><span data-stu-id="9d32e-116">30000</span></span> | <span data-ttu-id="9d32e-117">13000</span><span class="sxs-lookup"><span data-stu-id="9d32e-117">13000</span></span> |
| <span data-ttu-id="9d32e-118">Ingebouwde opdracht analyse cache:`powershell -command "Unknown-Command"`</span><span class="sxs-lookup"><span data-stu-id="9d32e-118">Command analysis cache built: `powershell -command "Unknown-Command"`</span></span> | <span data-ttu-id="9d32e-119">7000</span><span class="sxs-lookup"><span data-stu-id="9d32e-119">7000</span></span> | <span data-ttu-id="9d32e-120">520</span><span class="sxs-lookup"><span data-stu-id="9d32e-120">520</span></span> |
| <code>1..1000000 &#124; % { }</code> | <span data-ttu-id="9d32e-121">1400</span><span class="sxs-lookup"><span data-stu-id="9d32e-121">1400</span></span> | <span data-ttu-id="9d32e-122">750</span><span class="sxs-lookup"><span data-stu-id="9d32e-122">750</span></span> |

> [!NOTE]
> <span data-ttu-id="9d32e-123">Een wijziging met betrekking tot het opstarten kan van invloed zijn op bepaalde niet-ondersteunde scenario's.</span><span class="sxs-lookup"><span data-stu-id="9d32e-123">One change related to startup might impact some unsupported scenarios.</span></span> <span data-ttu-id="9d32e-124">Power shell leest de bestanden `$pshome\*.ps1xml` niet meer, omdat deze bestanden zijn geconverteerd naar C# om te voor komen dat bestanden en CPU-overhead voor het verwerken van de XML-bestanden worden verwerkt.</span><span class="sxs-lookup"><span data-stu-id="9d32e-124">PowerShell no longer reads the files `$pshome\*.ps1xml` -- these files have been converted to C# to avoid some file and CPU overhead of processing the XML files.</span></span> <span data-ttu-id="9d32e-125">De bestanden bestaan nog steeds voor de ondersteuning van v2 naast elkaar, dus als u de bestands inhoud wijzigt, heeft dit geen effect op V5, alleen v2.</span><span class="sxs-lookup"><span data-stu-id="9d32e-125">The files still exist to support V2 side-by-side, so if you change the file contents, it will not have any effect to V5, only V2.</span></span> <span data-ttu-id="9d32e-126">Houd er rekening mee dat het wijzigen van de inhoud van deze bestanden nooit een ondersteund scenario was.</span><span class="sxs-lookup"><span data-stu-id="9d32e-126">Note that changing the contents of these files was never a supported scenario.</span></span>

<span data-ttu-id="9d32e-127">Een andere zicht bare wijziging is hoe Power shell de geëxporteerde opdrachten en andere informatie voor modules die op een systeem zijn geïnstalleerd, in de cache opslaat.</span><span class="sxs-lookup"><span data-stu-id="9d32e-127">Another visible change is how PowerShell caches the exported commands and other information for modules that are installed on a system.</span></span> <span data-ttu-id="9d32e-128">Voorheen werd deze cache opgeslagen in de map `$env:LOCALAPPDATA\Microsoft\Windows\PowerShell\CommandAnalysis`.</span><span class="sxs-lookup"><span data-stu-id="9d32e-128">Previously, this cache was stored in the directory `$env:LOCALAPPDATA\Microsoft\Windows\PowerShell\CommandAnalysis`.</span></span> <span data-ttu-id="9d32e-129">In WMF 5,1 is de cache één bestand `$env:LOCALAPPDATA\Microsoft\Windows\PowerShell\ModuleAnalysisCache`.</span><span class="sxs-lookup"><span data-stu-id="9d32e-129">In WMF 5.1, the cache is a single file `$env:LOCALAPPDATA\Microsoft\Windows\PowerShell\ModuleAnalysisCache`.</span></span> <span data-ttu-id="9d32e-130">Zie [module analyse cache](release-notes.md#module-analysis-cache) voor meer informatie.</span><span class="sxs-lookup"><span data-stu-id="9d32e-130">See [Module Analysis Cache](release-notes.md#module-analysis-cache) for more details.</span></span>